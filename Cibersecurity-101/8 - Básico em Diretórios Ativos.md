# Crescimento de Redes e Domínios no Windows

Imagine que você está administrando a rede de uma pequena empresa com apenas cinco computadores e cinco funcionários. Em uma rede tão pequena, provavelmente você conseguirá configurar cada computador separadamente sem grandes problemas. 

Você fará login manualmente em cada máquina, criará usuários para quem for utilizá-las e aplicará configurações específicas para cada conta de funcionário. Se o computador de um usuário parar de funcionar, você provavelmente irá até o local e consertará o problema presencialmente.

Embora isso pareça um estilo de vida bastante tranquilo, imagine que sua empresa cresceu repentinamente e agora possui **157 computadores e 320 usuários diferentes**, distribuídos em **quatro escritórios distintos**. Você ainda conseguiria gerenciar cada computador separadamente, configurar políticas manualmente para cada usuário da rede e oferecer suporte presencial para todos? A resposta muito provavelmente é **não**.

Para superar essas limitações, podemos usar um **domínio Windows**. Simplificando, um domínio Windows é um **grupo de usuários e computadores sob a administração de uma empresa**. A principal ideia por trás de um domínio é **centralizar a administração dos componentes comuns de uma rede de computadores Windows** em um único repositório chamado **Active Directory (AD)**.

O servidor que executa os serviços do Active Directory é conhecido como **Controlador de Domínio (Domain Controller - DC)**.

## Vantagens de um Domínio Windows

### Principais Vantagens de um Domínio Windows

- **Gerenciamento centralizado de identidades**: Todos os usuários da rede podem ser configurados a partir do Active Directory com o mínimo de esforço.
- **Gerenciamento de políticas de segurança**: É possível configurar políticas de segurança diretamente no Active Directory e aplicá-las aos usuários e computadores da rede conforme necessário.

---

### Um Exemplo do Mundo Real

Se isso parece um pouco confuso, é bem provável que você já tenha interagido com um domínio Windows em algum momento, seja na escola, universidade ou no trabalho.

Em redes escolares ou universitárias, geralmente você recebe um nome de usuário e uma senha que podem ser usados em qualquer computador disponível no campus. Suas credenciais são válidas em todas as máquinas porque, sempre que você as digita em um computador, o processo de autenticação é redirecionado para o Active Directory, onde elas serão verificadas. 

Graças ao Active Directory, suas credenciais **não precisam estar armazenadas em cada máquina** e ficam disponíveis em toda a rede.

O Active Directory também é o componente responsável por **restringir o acesso ao Painel de Controle** e outras áreas sensíveis nas máquinas da escola ou universidade. As políticas geralmente são aplicadas em toda a rede, impedindo que você tenha privilégios administrativos nesses computadores.

---

### Bem-vindo à THM Inc.

Durante esta tarefa, assumiremos o papel do novo administrador de TI da **THM Inc.**. Como nossa primeira missão, nos foi solicitado revisar o domínio atual "**THM.local**" e fazer algumas configurações adicionais.

Você terá **credenciais administrativas** sobre um **Controlador de Domínio (Domain Controller - DC)** pré-configurado para realizar essas atividades.

# O Núcleo de um Domínio Windows: Active Directory Domain Services (AD DS)

O núcleo de qualquer domínio Windows é o serviço **Active Directory Domain Services (AD DS)**. Esse serviço atua como um catálogo que armazena informações de todos os "objetos" existentes na rede. Entre os muitos objetos suportados pelo AD, temos:

- Usuários
- Grupos
- Máquinas
- Impressoras
- Compartilhamentos (shares)
- Entre outros

---

## Usuários

Os usuários são um dos tipos de objetos mais comuns no Active Directory. Eles pertencem à categoria de **principais de segurança (security principals)**, o que significa que podem ser autenticados pelo domínio e receber permissões sobre recursos, como arquivos e impressoras.

Usuários podem representar dois tipos de entidades:

- **Pessoas**: usuários geralmente representam colaboradores da organização que precisam acessar a rede.
- **Serviços**: alguns usuários são criados para rodar serviços, como IIS ou MSSQL. Cada serviço precisa de um usuário, que possui apenas os privilégios necessários para executar sua função específica.

---

## Máquinas

As **máquinas** são outro tipo de objeto no Active Directory. Para cada computador que se junta ao domínio, um **objeto de máquina** é criado. Máquinas também são consideradas **principais de segurança** e recebem uma conta, assim como os usuários.

- Essas contas têm direitos limitados no domínio.
- A própria máquina é a administradora local do sistema.
- Essas contas **não devem ser acessadas por humanos**, mas se a senha for conhecida, o login é possível.
- As **senhas dessas contas são rotacionadas automaticamente** e geralmente têm **120 caracteres aleatórios**.

### Como identificar contas de máquinas?

As contas seguem um padrão específico: o nome do computador seguido de um cifrão `$`.  
**Exemplo:** Um computador chamado `DC01` terá uma conta de máquina chamada `DC01$`.

---

## Grupos de Segurança

Se você já usou o Windows, sabe que é possível criar **grupos de usuários** para conceder acesso a arquivos ou outros recursos. Isso facilita o gerenciamento, pois ao adicionar um usuário a um grupo, ele herda automaticamente todas as permissões do grupo.

- Grupos de segurança também são **principais de segurança**.
- Podem conter **usuários e máquinas** como membros.
- Grupos podem conter **outros grupos** (aninhamento).

---

### Grupos de Segurança Padrão em um Domínio

| **Grupo de Segurança** | **Descrição** |
|------------------------|---------------|
| **Domain Admins**      | Têm privilégios administrativos sobre todo o domínio. Por padrão, podem administrar qualquer computador, incluindo os Controladores de Domínio (DCs). |
| **Server Operators**   | Podem administrar os DCs, mas **não** podem alterar membros de grupos administrativos. |
| **Backup Operators**   | Podem acessar qualquer arquivo ignorando permissões, utilizados para realizar backups. |
| **Account Operators**  | Podem criar ou modificar outras contas no domínio. |
| **Domain Users**       | Inclui todas as contas de usuário existentes no domínio. |
| **Domain Computers**   | Inclui todos os computadores do domínio. |
| **Domain Controllers** | Inclui todos os controladores de domínio (DCs) no domínio. |

## Organizational Units (OUs)

Ao abrir a janela do Active Directory, você poderá visualizar a **hierarquia de usuários, computadores e grupos** existentes no domínio. Esses objetos são organizados em **Unidades Organizacionais (Organizational Units – OUs)**, que são **objetos contêineres** usados para classificar usuários e máquinas.

### Para que servem as OUs?

As OUs são utilizadas principalmente para **agrupar usuários com requisitos de políticas semelhantes**. Por exemplo:

- Pessoas do **departamento de Vendas** podem ter um conjunto de políticas diferentes das pessoas do **departamento de TI**.
- Isso permite **aplicar políticas específicas por departamento** (como acesso a recursos, configurações de segurança, permissões etc.).

> ⚠️ **Importante:** Um usuário **só pode pertencer a uma única OU por vez.**

### Exemplo prático:
- A OU "Financeiro" pode conter apenas os usuários e máquinas do setor financeiro.
- A OU "TI" pode conter os administradores e os servidores usados pela equipe de tecnologia.

Esse agrupamento facilita a administração centralizada e a aplicação de **GPOs (Group Policy Objects)** específicas para cada conjunto de usuários ou computadores.


