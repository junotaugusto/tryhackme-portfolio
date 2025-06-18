# Protocolo de Transferência de Arquivos (FTP)

Diferente do HTTP, que é projetado para recuperar páginas da web, o **FTP (File Transfer Protocol)** é projetado especificamente para transferir arquivos. Por isso, o FTP é muito eficiente nesse tipo de tarefa e, quando todas as condições são iguais, pode atingir velocidades mais altas do que o HTTP.

## Comandos comuns do protocolo FTP:

- `USER`: usado para inserir o nome de usuário.
- `PASS`: usado para digitar a senha.
- `RETR`: (retrieve) utilizado para **baixar** um arquivo do servidor FTP para o cliente.
- `STOR`: (store) utilizado para **enviar** um arquivo do cliente para o servidor FTP.

O servidor FTP escuta, por padrão, na **porta TCP 21**. A transferência de dados é feita através de **outra conexão separada** iniciada pelo cliente com o servidor.

---

## Exemplo de uso no terminal

No terminal abaixo, executamos o comando `ftp 10.10.253.240` para conectar a um servidor FTP remoto usando o cliente local FTP. Em seguida, seguimos os seguintes passos:

1. Utilizamos o nome de usuário `anonymous` para logar.
2. Não foi necessário fornecer senha.
3. Usamos o comando `ls` para listar os arquivos disponíveis para download.
4. Usamos `type ascii` para mudar para o modo ASCII (já que é um arquivo de texto).
5. Por fim, usamos `get coffee.txt` para baixar o arquivo desejado.

### Terminal
user@TryHackMe$ ftp 10.10.253.240<br>
Connected to 10.10.253.240 (10.10.253.240).<br>
220 (vsFTPd 3.0.5)<br>
Name (10.10.253.240:strategos): anonymous<br>
331 Please specify the password.<br>
Password:<br>
230 Login successful.<br>
Remote system type is UNIX.<br>
Using binary mode to transfer files.<br>
ftp> ls<br>
227 Entering Passive Mode (10,10,41,192,134,10).<br>
150 Here comes the directory listing.<br>
-rw-r--r-- 1 0 0 1480 Jun 27 08:03 coffee.txt<br>
-rw-r--r-- 1 0 0 14 Jun 27 08:04 flag.txt<br>
-rw-r--r-- 1 0 0 1595 Jun 27 08:05 tea.txt<br>
226 Directory send OK.<br>
ftp> type ascii<br>
200 Switching to ASCII mode.<br>
ftp> get coffee.txt<br>
local: coffee.txt remote: coffee.txt<br>
227 Entering Passive Mode (10,10,41,192,57,100).<br>
150 Opening BINARY mode data connection for coffee.txt (1480 bytes).<br>
WARNING! 47 bare linefeeds received in ASCII mode<br>
File may not have transferred correctly.<br>
226 Transfer complete.<br>
1480 bytes received in 8e-05 secs (18500.00 Kbytes/sec)<br>
ftp> quit<br>
221 Goodbye.<br>


> ⚠️ **Nota:** o modo ASCII pode causar problemas com arquivos que não estejam formatados como texto simples. A mensagem de *WARNING* indica isso.

---

## Análise com o Wireshark

Usamos o **Wireshark** para examinar mais de perto as mensagens trocadas entre cliente e servidor. As mensagens enviadas pelo **cliente** aparecem em **vermelho**, e as respostas do **servidor** em **azul**.

Note que os comandos digitados pelo usuário nem sempre são enviados ao servidor com o mesmo nome. Por exemplo, ao digitar `ls`, o cliente envia o comando `LIST` ao servidor.

Outro detalhe importante: **tanto a listagem de diretório quanto o arquivo baixado são transferidos por conexões separadas**, distintas da conexão principal de controle (porta 21).

![alt text](/Cibersecurity-101/Network%20Core%20Protocols/IMAGENS/FTP.png)

No exercício em questão, o Try Hack Me pede para pegar, pelo meio do FTP, o arquivo flag.txt, feito da seguinte maneira:
"get flag.txt"
Saia do FTP e utilize o comando CAT para ler o conteúdo do arquivo de texto.


