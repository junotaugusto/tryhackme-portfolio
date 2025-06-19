# Adicionando TLS ao SMTP, POP3 e IMAP

Adicionar TLS ao SMTP, POP3 e IMAP não é diferente de adicionar TLS ao HTTP. De forma semelhante ao HTTP, que recebe um "S" adicional para se tornar **HTTPS** (Hypertext Transfer Protocol Secure), os protocolos **SMTP**, **POP3** e **IMAP** tornam-se **SMTPS**, **POP3S** e **IMAPS**, respectivamente.

Usar esses protocolos sobre TLS não é diferente de usar HTTP sobre TLS; portanto, **quase todos os pontos discutidos sobre o HTTPS também se aplicam a esses protocolos**.

---

## Portas padrão para as versões inseguras (sem TLS):

| Protocolo | Porta Padrão |
|-----------|---------------|
| HTTP      | 80            |
| SMTP      | 25            |
| POP3      | 110           |
| IMAP      | 143           |

*Essas portas transmitem os dados em texto claro, ou seja, sem criptografia.*

---

## Portas padrão para as versões seguras (com TLS):

| Protocolo | Porta Padrão |
|-----------|---------------|
| HTTPS     | 443           |
| SMTPS     | 465 e 587     |
| POP3S     | 995           |
| IMAPS     | 993           |

*Essas portas realizam a comunicação criptografada via TLS, protegendo o conteúdo transmitido.*

---

O TLS pode ser adicionado a muitos outros protocolos; o raciocínio e as vantagens seriam semelhantes: **confidencialidade, integridade e autenticidade da comunicação**.
