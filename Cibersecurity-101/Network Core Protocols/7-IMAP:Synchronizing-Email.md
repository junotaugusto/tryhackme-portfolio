# 🔄 Sincronizando E-mails com IMAP e Telnet

O protocolo **POP3** funciona bem quando você acessa seus e-mails **de um único dispositivo** (por exemplo, seu cliente de e-mail no computador pessoal).  
Mas… e se você quiser ler seus e-mails no **computador do trabalho, no notebook e também no celular**?

É aí que entra o **IMAP** — *Internet Message Access Protocol*.

---

## 📧 Por que usar IMAP?

Com o IMAP, sua caixa de entrada permanece **sincronizada entre todos os dispositivos**.  
Ao contrário do POP3, que baixa e apaga os e-mails do servidor, o IMAP **mantém os e-mails no servidor** e sincroniza alterações como:
- Lidos
- Movidos
- Deletados

> 🟰 IMAP oferece uma experiência **muito mais integrada** quando se usa múltiplos dispositivos ou webmail.

---

## 🧾 Comparação Rápida

| Protocolo | Armazena localmente? | Sincroniza entre dispositivos? | Usa mais espaço no servidor? |
|----------|----------------------|-------------------------------|------------------------------|
| POP3     | ✅ Sim               | ❌ Não                         | ❌ Menos                     |
| IMAP     | ❌ Não               | ✅ Sim                         | ✅ Mais                      |

---

## 🔧 Comandos IMAP comuns

Os comandos IMAP são mais detalhados e técnicos do que os do POP3. Veja alguns exemplos:

- `LOGIN <username> <password>` → autentica o usuário
- `SELECT <mailbox>` → escolhe a pasta (ex: inbox)
- `FETCH <número> <dados>` → busca o conteúdo da mensagem
   - Exemplo: `FETCH 3 body[]` → busca o corpo da mensagem número 3
- `MOVE <mensagens> <caixa>` → move as mensagens para outra pasta
- `COPY <mensagens> <caixa>` → copia as mensagens para outra pasta
- `LOGOUT` → encerra a sessão

---

## 🧪 Exemplo: Sessão IMAP com Telnet

O IMAP usa a porta TCP **143** por padrão. No exemplo abaixo, conectamos ao servidor com `telnet` e buscamos uma mensagem.

### Terminal
user@TryHackMe$ telnet 10.10.41.192 143<br>
Trying 10.10.41.192...<br>
Connected to 10.10.41.192.<br>
Escape character is '^]'.<br>

OK [CAPABILITY IMAP4rev1 SASL-IR LOGIN-REFERRALS ID ENABLE IDLE LITERAL+ STARTTLS AUTH=PLAIN] Dovecot (Ubuntu) ready.<br>
A LOGIN strategos<br>
A OK [CAPABILITY IMAP4rev1 ...] Logged in<br>
B SELECT inbox<br>

FLAGS (\Answered \Flagged \Deleted \Seen \Draft)<br>

OK [PERMANENTFLAGS (\Answered \Flagged \Deleted \Seen \Draft *)] Flags permitted.<br>

4 EXISTS<br>

0 RECENT<br>

OK [UNSEEN 2] First unseen.<br>

OK [UIDVALIDITY 1719824692] UIDs valid<br>

OK [UIDNEXT 5] Predicted next UID<br>
B OK [READ-WRITE] Select completed (0.001 + 0.000 secs).<br>
C FETCH 3 body[]<br>

3 FETCH (BODY[] {445}<br>
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
)<br>
C OK Fetch completed (0.001 + 0.000 secs).<br>
D LOGOUT<br>

BYE Logging out<br>
D OK Logout completed (0.001 + 0.000 secs).<br>
Connection closed by foreign host.<br>


---

## 📊 Wireshark: Visualizando o Tráfego

A captura do Wireshark abaixo mostra a troca entre o cliente e o servidor IMAP.  
- Os **comandos enviados pelo cliente** (ex: `LOGIN`, `FETCH`, etc.) aparecem em **vermelho**
- As **respostas longas do servidor** aparecem em **azul**

![alt text](/Cibersecurity-101/Network%20Core%20Protocols/IMAGENS/IMAP.png)

> 🔍 Neste exemplo, bastaram **quatro comandos** para autenticar, selecionar a caixa, buscar a mensagem e sair.

---

## 🔐 Considerações de Segurança

- O IMAP, como o POP3, também pode trafegar **sem criptografia** se não for usado com STARTTLS ou IMAPS (porta 993)
- Capturar senhas com ferramentas como Wireshark é possível se o tráfego não estiver protegido.