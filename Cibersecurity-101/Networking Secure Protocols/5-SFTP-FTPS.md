## SFTP e FTPS

SFTP significa **SSH File Transfer Protocol** e permite a transferência segura de arquivos. Ele faz parte do conjunto de protocolos do SSH e compartilha o mesmo número de porta, **22**. 

Se estiver habilitado na configuração do servidor OpenSSH, você pode se conectar usando um comando como **sftp nome-de-usuário@nome-do-host**.

Depois de fazer login, você pode emitir comandos como:
- `get nome-do-arquivo` para **baixar arquivos**
- `put nome-do-arquivo` para **enviar arquivos**

De modo geral, os comandos do SFTP são semelhantes aos do Unix e podem diferir dos comandos do FTP.

**SFTP não deve ser confundido com FTPS.**

Você está certo em pensar que **FTPS** significa **File Transfer Protocol Secure**. Como o FTPS é protegido? Sim, você está correto ao estimar que ele é protegido usando **TLS**, assim como o HTTPS.

- Enquanto o **FTP** usa a porta **21**
- O **FTPS** geralmente usa a porta **990**

O FTPS requer configuração de certificado emitido por uma autoridade certificados, para garantir a identidade do servidor e permitir criptografia segura. 

Além disso, pode ser complicado de permitir através de firewalls rígidos, já que ele utiliza conexões separadas para controle e transferência de dados, ou seja, o FTPS usa uma conexão para enviar comandos (como login, navegação de pastas) e outra para transferir os arquivos em si. Isso complica o tráfego em redes com firewall, porque o firewall precisa entender e permitir múltiplas conexões dinâmicas, o que pode exigir configuração adicional ou causar bloqueios.

**Configurar um servidor SFTP é tão simples quanto habilitar uma opção no servidor OpenSSH.**  
Assim como o HTTPS, SMTPS, POP3S, IMAPS e outros protocolos que dependem do TLS para segurança, o FTPS requer um certificado TLS adequado para funcionar de forma segura.


