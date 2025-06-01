# Autenticação em Domínios Windows

Quando utilizamos domínios Windows, todas as **credenciais dos usuários** são armazenadas nos **Controladores de Domínio** (Domain Controllers). Sempre que um usuário tenta se autenticar em algum serviço usando credenciais do domínio, o serviço precisa consultar o Domain Controller para verificar se essas credenciais são válidas.

Existem dois protocolos que podem ser utilizados para autenticação em rede em domínios Windows:

- **Kerberos**: É o protocolo padrão e utilizado por qualquer versão moderna do Windows.
- **NetNTLM**: Protocolo de autenticação legado, mantido apenas por questões de compatibilidade com sistemas antigos.

> ⚠️ Embora o NetNTLM seja considerado obsoleto, a maioria das redes ainda mantém ambos os protocolos ativos.

## 🔐 Autenticação Kerberos

O **Kerberos** é o protocolo de autenticação padrão nas versões mais recentes do Windows. Ele oferece uma maneira segura e eficiente de autenticar usuários em uma rede sem precisar reenviar suas credenciais repetidamente.

---

### 🎟️ Conceito de "Tickets"

Usuários que se autenticam com Kerberos recebem **tickets**, que funcionam como um **comprovante de autenticação** anterior. Eles podem apresentar esses tickets a serviços da rede como prova de que já foram autenticados.

---

### 🧭 Etapas do Processo de Autenticação com Kerberos

#### 1. Solicitação Inicial ao KDC

- O usuário envia **seu nome de usuário e um timestamp**, criptografado com uma chave derivada de sua senha, para o **KDC (Key Distribution Center)**.
- O **KDC** é normalmente executado no **Controlador de Domínio (Domain Controller)** e é responsável por gerar os tickets Kerberos.

#### 2. Emissão do TGT (Ticket Granting Ticket)

- O KDC responde com um **TGT (Ticket Granting Ticket)** e uma **Chave de Sessão (Session Key)**.
- O **TGT** permite que o usuário solicite outros tickets para acessar serviços específicos na rede **sem precisar reenviar suas credenciais**.
- O TGT é **criptografado usando o hash da conta `krbtgt`**, então o usuário não pode ver seu conteúdo.
- O TGT contém uma cópia da Chave de Sessão. O KDC pode recuperá-la a qualquer momento descriptografando o TGT, por isso **não precisa armazenar a chave** separadamente.

---

### 🧾 Solicitação de Acesso a um Serviço

Quando o usuário quer se conectar a um serviço (como um compartilhamento de arquivos, site ou banco de dados):

#### 3. Solicitação de TGS (Ticket Granting Service)

- O usuário envia ao KDC:
  - **Seu nome de usuário e um timestamp**, agora criptografado com a **Chave de Sessão** recebida antes.
  - O **TGT**.
  - Um **SPN (Service Principal Name)**, que identifica o serviço e o servidor que deseja acessar.

#### 4. Emissão do TGS

- O KDC responde com:
  - Um **TGS (Ticket Granting Service)**: um ticket válido apenas para o serviço solicitado.
  - Uma nova **Chave de Sessão de Serviço (Service Session Key)**, usada para comunicação com o serviço.

- O **TGS é criptografado com uma chave derivada do hash da conta do "Service Owner"** — ou seja, a conta (usuário ou máquina) sob a qual o serviço está sendo executado.
- O TGS inclui uma cópia da **Chave de Sessão de Serviço** criptografada, que só pode ser acessada pelo **Service Owner** ao descriptografar o TGS.

---

### 📌 Resumo Visual


    participant Usuário
    participant KDC
    participant Serviço

    Usuário->>KDC: Solicita TGT (user + timestamp)
    KDC-->>Usuário: TGT + Session Key

    Usuário->>KDC: Solicita TGS (com TGT, SPN, timestamp criptografado)
    KDC-->>Usuário: TGS + Service Session Key

    Usuário->>Serviço: Apresenta TGS + autenticação
    Serviço-->>Usuário: Acesso autorizado


## 🔐 Autenticação NetNTLM

O **NetNTLM** é um protocolo legado de autenticação baseado em um mecanismo de **desafio e resposta (challenge-response)**.

Embora seja menos seguro que o Kerberos, ele ainda é suportado por compatibilidade com sistemas mais antigos.

### 🔁 Como funciona o processo de autenticação com NetNTLM:

1. O **cliente** envia uma **solicitação de autenticação** para o servidor que deseja acessar.

2. O **servidor gera um número aleatório** (chamado de "desafio") e o envia de volta para o cliente.

3. O cliente então **combina o hash de sua senha NTLM com o desafio**, junto com outros dados conhecidos, e gera uma **resposta** para esse desafio.

4. O cliente envia essa resposta de volta ao servidor.

5. O servidor **encaminha o desafio e a resposta para o Controlador de Domínio (Domain Controller)** para verificar se estão corretos.

6. O Domain Controller utiliza o mesmo desafio e o hash da senha armazenado para **recalcular a resposta esperada** e a compara com a resposta enviada pelo cliente:
   - Se as respostas forem iguais, o cliente é **autenticado com sucesso**.
   - Caso contrário, o acesso é negado.

7. O **resultado da autenticação** é enviado do Domain Controller para o servidor, que por sua vez encaminha a resposta para o cliente.

> 🔒 Importante: A **senha do usuário (ou seu hash)** **nunca é transmitida pela rede**, o que aumenta a segurança desse processo, mesmo sendo um protocolo antigo.

---

### 🧠 Observação sobre contas locais

Se a autenticação for feita **com uma conta local (e não do domínio)**, o **próprio servidor** pode verificar a resposta ao desafio **sem precisar consultar o Domain Controller**. Isso acontece porque o servidor **armazena localmente o hash da senha** na sua **SAM (Security Account Manager)**.

---

Mesmo sendo um protocolo antigo, o NetNTLM ainda está presente em muitas redes. Por isso, é importante conhecê-lo tanto para administração quanto para segurança (por exemplo, entender vetores de ataque como Pass-the-Hash ou relay attacks).

