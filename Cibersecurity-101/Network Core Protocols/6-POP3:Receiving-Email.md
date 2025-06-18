# 📥 Recebendo E-mails com POP3 e Telnet

Depois de enviar um e-mail, você provavelmente quer acessá-lo no seu cliente local de e-mails. Para isso, é usado o **POP3** — *Post Office Protocol version 3*, um protocolo que permite que o cliente de e-mail se conecte a um servidor e **recupere mensagens**.

---

## ✉️ SMTP vs POP3: Qual a Diferença?

Sem entrar nos detalhes técnicos mais profundos:

- **SMTP**: envia mensagens → como **entregar uma carta no correio**.
- **POP3**: baixa mensagens → como **abrir sua caixa de correio pessoal**.

> 💬 Pense assim:
> - **SMTP** = caixa de coleta dos Correios.
> - **POP3** = sua caixinha de cartas na frente de casa.

![alt text](POP3-1.png)

## 🔧 Comandos POP3 mais usados

Estes são alguns dos comandos mais comuns em uma sessão POP3:

- `USER <username>` → identifica o usuário
- `PASS <password>` → fornece a senha do usuário
- `STAT` → retorna número total de mensagens e tamanho
- `LIST` → lista todas as mensagens e seus tamanhos
- `RETR <número>` → recupera a mensagem especificada
- `DELE <número>` → marca a mensagem para exclusão
- `QUIT` → encerra a sessão e aplica alterações (como deleções)

---

## 🧪 Exemplo: Sessão POP3 com Telnet

POP3 usa a porta TCP **110** por padrão. No exemplo abaixo, é usada uma conexão `telnet` para recuperar a mensagem enviada no exemplo anterior.

### Terminal
user@TryHackMe$ telnet 10.10.253.240 110<br>
Trying 10.10.253.240...<br>
Connected to 10.10.253.240.<br>
Escape character is '^]'.<br>
+OK [XCLIENT] Dovecot (Ubuntu) ready.<br>
AUTH<br>
+OK<br>
PLAIN<br>
.<br>
USER strategos<br>
+OK<br>
PASS <br>
+OK Logged in.<br>
STAT<br>
+OK 3 1264<br>
LIST<br>
+OK 3 messages:<br>
1 407<br>
2 412<br>
3 445<br>
.<br>
RETR 3<br>
+OK 445 octets<br>
Return-path: user@client.thm<br>
Envelope-to: strategos@server.thm<br>
Delivery-date: Thu, 27 Jun 2024 16:19:35 +0000<br>
Received: from [10.11.81.126] (helo=client.thm)<br>
    by example.thm with smtp (Exim 4.95)<br>
    (envelope-from user@client.thm)<br>
    id 1sMrpq-0001Ah-UT<br>
    for strategos@server.thm;<br>
    Thu, 27 Jun 2024 16:19:35 +0000<br>
From: user@client.thm<br>
To: strategos@server.thm<br>
Subject: Telnet email<br>
<br>
Hello. I am using telnet to send you an email!<br>
.<br>
QUIT<br>
+OK Logging out.<br>
Connection closed by foreign host.<br>


---

## 🔐 Segurança: Alerta Importante!

> ⚠️ **As comunicações POP3 acontecem em texto puro por padrão**.

Isso significa que qualquer pessoa monitorando a rede (com ferramentas como Wireshark) pode **ver senhas e conteúdo de mensagens**, como mostra a imagem abaixo:

![alt text](POP3-2.png)

As capturas do Wireshark distinguem:
- **Comandos do cliente** → em vermelho
- **Respostas do servidor** → em azul

---

## 🔑 Credenciais de Acesso (quando necessário)

Ao se conectar a um servidor POP3, é necessário autenticar-se. Use as seguintes credenciais:

- **Usuário:** `linda`
- **Senha:** `Pa$$123`

---

## 🧠 Conclusão

POP3 é um protocolo simples e direto para baixar mensagens de e-mail. Apesar de ser eficiente, **não é seguro sem criptografia**. Sempre prefira conexões **POP3S (POP3 sobre SSL/TLS)** em ambientes reais.
