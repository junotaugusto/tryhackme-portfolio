# Sistema de Nomes de Domínio (DNS)

Você se lembra dos endereços IP dos seus sites favoritos? A menos que seja um endereço IP privado de um dispositivo local, ninguém precisa se preocupar em memorizar endereços IP. Isso se deve, em parte, ao **Sistema de Nomes de Domínio (DNS)**, que é responsável por mapear corretamente um nome de domínio para um endereço IP.

> 💡 **Comentário:** O DNS atua como uma "agenda telefônica" da internet, convertendo nomes fáceis de lembrar (como `example.com`) em endereços IP que as máquinas usam para se comunicar.

## Funcionamento do DNS

O DNS opera na **Camada de Aplicação** (Application Layer), ou seja, na **Camada 7 do modelo ISO/OSI**. O tráfego DNS usa, por padrão, a **porta UDP 53**, e como alternativa de fallback, a **porta TCP 53**.

> 💡 **Comentário:** UDP é preferido por ser mais rápido e leve; TCP é usado quando há necessidade de confiabilidade ou quando a resposta excede o tamanho do pacote UDP.

Existem vários tipos de registros DNS. Neste exercício, focaremos em quatro principais:

- **Registro A (Address):** Mapeia um nome de host para um ou mais endereços IPv4.  
  Exemplo: `example.com` pode ser resolvido para `172.17.2.172`.

- **Registro AAAA (quad-A):** Semelhante ao Registro A, mas para endereços **IPv6**.  
  
- **Registro CNAME (Canonical Name):** Mapeia um nome de domínio para outro nome de domínio.  
  Exemplo: `www.example.com` pode apontar para `example.com` ou até mesmo `example.org`.

- **Registro MX (Mail Exchange):** Especifica o servidor de e-mail responsável por lidar com os e-mails de um domínio.

> 💡 **Comentário:** Navegar até `example.com` envolve uma consulta DNS para o Registro A. Já enviar um e-mail para `test@example.com` requer uma consulta DNS para o Registro MX.

---

## Usando o Terminal: Consultas com `nslookup`

Se você quiser consultar o endereço IP de um domínio a partir do terminal, pode usar a ferramenta `nslookup`. Veja o exemplo abaixo:

### Terminal

user@TryHackMe$ nslookup www.example.com<br>
Server: 127.0.0.53<br>
Address: 127.0.0.53#53<br>
<br>
Non-authoritative answer:<br>
Name: www.example.com<br>
Address: 93.184.215.14<br>
Name: www.example.com<br>
Address: 2606:2800:21f:cb07:6820:80da:af6b:8b2c<br>


> 💡 **Comentário:** A resposta inclui um endereço IPv4 (registro A) e um IPv6 (registro AAAA).

---

## Captura de Pacotes DNS

A consulta acima resultou em **quatro pacotes**. No terminal abaixo, vemos que o **primeiro** e o **terceiro** pacotes são consultas DNS para os registros A e AAAA, respectivamente. O **segundo** e o **quarto** são as respostas dessas consultas.

### Terminal

user@TryHackMe$ tshark -r dns-query.pcapng -Nn<br>
1 0.000000000 192.168.66.89 → 192.168.66.1 DNS 86 Standard query 0x2e0f A www.example.com OPT<br>
2 0.059049584 192.168.66.1 → 192.168.66.89 DNS 102 Standard query response 0x2e0f A www.example.com A 93.184.215.14 OPT<br>
3 0.059721705 192.168.66.89 → 192.168.66.1 DNS 86 Standard query 0x96e1 AAAA www.example.com OPT<br>
4 0.101568276 192.168.66.1 → 192.168.66.89 DNS 114 Standard query response 0x96e1 AAAA www.example.com AAAA 2606:2800:21f:cb07:6820:80da:af6b:8b2c OPT<br>


> 🧪 **Comentário:** Esses pacotes foram analisados com o `tshark`, uma ferramenta de linha de comando para leitura de arquivos `.pcapng`. Observe que o cliente (`192.168.66.89`) faz duas consultas (A e AAAA) e recebe as respostas do servidor DNS (`192.168.66.1`).

---

## Resumo

- O DNS é essencial para a navegação na internet.
- Usa portas 53 UDP/TCP.
- Os principais tipos de registros são: A, AAAA, CNAME e MX.
- Ferramentas como `nslookup` e `tshark` permitem investigar como funciona a resolução de nomes.

---
