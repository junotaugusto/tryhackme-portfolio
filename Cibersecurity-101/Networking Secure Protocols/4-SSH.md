# SSH: Uma Alternativa Segura ao Telnet

Usamos o protocolo TELNET na sala Networking Concepts. Embora seja muito conveniente para fazer login e administrar sistemas remotos, é arriscado quando todo o tráfego é **enviado em texto claro**. É fácil para qualquer pessoa monitorando o tráfego de rede obter suas credenciais de login assim que você usar telnet. Esse problema exigiu uma solução. 

**Tatu Ylönen** desenvolveu o protocolo Secure Shell (SSH) e lançou o SSH-1 em 1995 como freeware. (Curiosamente, foi o mesmo ano em que a Netscape Communications lançou o protocolo SSL 2.0.) 

Uma versão mais segura, o SSH-2, foi definida em 1996. Em 1999, os desenvolvedores do OpenBSD lançaram o OpenSSH, uma implementação de código aberto do SSH. Hoje em dia, quando você usa um cliente SSH, é muito provável que ele seja baseado nas bibliotecas e no código-fonte do **OpenSSH**.

O OpenSSH oferece vários benefícios. Vamos listar alguns pontos principais:

- **Autenticação segura**: além da autenticação baseada em senha, o SSH suporta autenticação por chave pública e autenticação de dois fatores.  
- **Confidencialidade**: o OpenSSH fornece criptografia de ponta a ponta, protegendo contra espionagem. Além disso, ele notifica você sobre novas chaves de servidor para proteger contra ataques man-in-the-middle.  
- **Integridade**: além de proteger a confidencialidade dos dados trocados, a criptografia também protege a integridade do tráfego.  
- **Túnel (Tunneling)**: o SSH pode criar um “túnel” seguro para encaminhar outros protocolos através do SSH. Essa configuração leva a uma conexão semelhante a uma VPN.  
- **Encaminhamento X11 (X11 Forwarding)**: se você se conectar a um sistema do tipo Unix com interface gráfica, o SSH permite que você use o aplicativo gráfico pela rede.

Você usaria o comando `ssh usuario@nome-do-host` para se conectar a um servidor SSH. 

Se o nome de usuário for o mesmo que o do seu login atual, você só precisa usar `ssh nome-do-host`, ou seja, se você estiver logado no seu computador como, por exemplo, fulano, e o servidor remoto também tiver um usuário com esse mesmo nome (fulano), então você não precisa digitar o nome de usuário no comando. O SSH vai presumir que o usuário remoto é o mesmo que o local. 

Em seguida, será solicitado que você insira uma senha; no entanto, **se for usada a autenticação por chave pública, você será conectado imediatamente.**<br> -> Antes de continuar, uma explicação sobre isso:

Existem duas formas de autenticação possíveis após tentar a conexão:
**Por senha:**<br>
O método padrão. Depois de enviar o comando SSH, o servidor vai pedir sua senha para permitir o acesso.
**Por meio de uma chave pública (public key authentication):**<br>
Se você já configurou uma chave pública no servidor e a chave privada correspondente está no seu computador, o SSH vai usá-la automaticamente.

Você não precisará digitar a senha — a autenticação é feita com base na correspondência entre a chave pública (no servidor) e a privada (no seu cliente/local). **É o que ocorre quando enviamos um commit com o 'git push' ao Github via SSH**

Lembrando aqui que o **usuário** refere-se ao nome da conta no servidor ao qual você quer se conectar e o **nome-do-host** pode ser o domínio (ex: meuservidor.com) ou o IP (ex: 192.168.1.10) do servidor.

A captura de tela abaixo mostra um exemplo de execução do Wireshark em um sistema Kali Linux remoto. O argumento `-X` é necessário para dar suporte à execução de interfaces gráficas, por exemplo  ssh 192.168.124.148 -X (o sistema local precisa ter um sistema gráfico apropriado instalado):

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/ssh.png)

Enquanto o servidor TELNET escuta a porta 23, o servidor SSH escuta a porta 23.

