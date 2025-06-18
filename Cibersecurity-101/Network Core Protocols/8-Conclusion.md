# 📡 Protocolos Fundamentais e suas Portas Padrão

No conteúdo anterior, falamos sobre o protocolo **TELNET**.  
Já nesta sequência, exploramos protocolos essenciais da comunicação em rede: **DNS**, **HTTP**, **FTP**, **SMTP**, **POP3** e **IMAP**.

Com isso, agora temos uma compreensão melhor de:

- Como nomes de domínio são resolvidos (DNS)
- Como páginas web são servidas (HTTP/HTTPS)
- Como e-mails são enviados (SMTP)
- Como e-mails são recebidos (POP3/IMAP)

---

> 🎯 **Objetivo principal:** entender como esses protocolos funcionam *por baixo dos panos*, além das interfaces gráficas dos navegadores ou clientes de e-mail.

---

## 🔢 Tabela de Protocolos e Portas Padrão

| **Protocolo** | **Protocolo de Transporte** | **Porta Padrão** |
|---------------|-----------------------------|------------------|
| TELNET        | TCP                         | 23               |
| DNS           | UDP ou TCP                  | 53               |
| HTTP          | TCP                         | 80               |
| HTTPS         | TCP                         | 443              |
| FTP           | TCP                         | 21               |
| SMTP          | TCP                         | 25               |
| POP3          | TCP                         | 110              |
| IMAP          | TCP                         | 143              |

---

> ✅ Essas portas são **valores padrão** — podem ser alteradas em ambientes específicos, mas são usadas pela maioria das aplicações por convenção.