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

