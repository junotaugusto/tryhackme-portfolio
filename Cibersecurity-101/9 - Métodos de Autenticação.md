# Autenticação em Domínios Windows

Quando utilizamos domínios Windows, todas as **credenciais dos usuários** são armazenadas nos **Controladores de Domínio** (Domain Controllers). Sempre que um usuário tenta se autenticar em algum serviço usando credenciais do domínio, o serviço precisa consultar o Domain Controller para verificar se essas credenciais são válidas.

Existem dois protocolos que podem ser utilizados para autenticação em rede em domínios Windows:

- **Kerberos**: É o protocolo padrão e utilizado por qualquer versão moderna do Windows.
- **NetNTLM**: Protocolo de autenticação legado, mantido apenas por questões de compatibilidade com sistemas antigos.

> ⚠️ Embora o NetNTLM seja considerado obsoleto, a maioria das redes ainda mantém ambos os protocolos ativos.

---

## 🛡️ Autenticação Kerberos

O **Kerberos** é o protocolo de autenticação padrão para sistemas Windows recentes. Usuários que se autenticam em serviços utilizando Kerberos recebem **tickets**. Esses tickets funcionam como uma **prova de autenticação anterior**. O usuário pode apresentar esse ticket a um serviço para mostrar que já foi autenticado anteriormente e, por isso, está autorizado a usar o serviço.

### 🔁 Como funciona o processo de autenticação com Kerberos:

1. O usuário envia seu **nome de usuário** e um **carimbo de data/hora (timestamp)**, ambos **criptografados com uma chave derivada de sua senha**, para o **KDC (Key Distribution Center)**.

   > O KDC é um serviço que normalmente está instalado no Domain Controller e é responsável por criar os tickets Kerberos.

2. O KDC responde com um **Ticket Granting Ticket (TGT)**. Esse TGT permitirá ao usuário solicitar outros tickets para acessar serviços específicos.

   > Parece estranho precisar de um ticket para obter mais tickets, mas isso é intencional: evita que o usuário tenha que enviar sua senha todas as vezes que quiser acessar um serviço.

3. Junto com o TGT, o usuário também recebe uma **Chave de Sessão (Session Key)**, que será usada para gerar os próximos pedidos de autenticação.

> 💡 O TGT é **criptografado com o hash da senha da conta `krbtgt`**, o que impede o usuário de visualizar seu conteúdo. Dentro do TGT está inclusa uma cópia da Session Key.

> O KDC não precisa armazenar essa chave de sessão, pois pode recuperá-la a qualquer momento descriptografando o TGT.

---

Esse processo torna o Kerberos um método de autenticação **mais seguro e eficiente**, pois minimiza o uso da senha diretamente e fornece um sistema de autenticação em cadeia baseado em tickets confiáveis.

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

