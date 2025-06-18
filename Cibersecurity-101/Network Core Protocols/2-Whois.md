# Registro de Domínio e Registros WHOIS

Na tarefa anterior, vimos como um nome de domínio é resolvido em um endereço IP. No entanto, para que isso aconteça, **alguém precisa ter autoridade para definir os registros DNS** como A, AAAA e MX, entre outros. Quem registra um nome de domínio recebe esse poder. Ou seja, se você registrar `example.com`, poderá definir quaisquer registros DNS válidos para esse domínio.

> 💡 **Comentário:** O registro de domínio dá ao titular o controle sobre as configurações que direcionam como o domínio será utilizado na internet — incluindo para onde ele aponta, quais servidores de e-mail o utilizam, etc.

---

## Registro de Domínio

Você pode registrar qualquer nome de domínio que esteja disponível por um ou mais anos. É necessário pagar uma **taxa anual** e fornecer **informações de contato precisas** como titular (registrante) do domínio.

Essas informações fazem parte dos dados disponíveis via **registros WHOIS** e, por padrão, são **públicas**.

> 🔤 **Comentário:** Apesar de ser escrito em letras maiúsculas, **WHOIS não é uma sigla**. Pronuncia-se "who is" (quem é), pois o objetivo é justamente identificar **quem registrou** um domínio.

Se você quiser registrar um domínio mas **não quiser expor suas informações de contato publicamente**, pode utilizar serviços de privacidade que ocultam seus dados dos registros WHOIS.

---

## Consultando Registros WHOIS

Você pode consultar os registros WHOIS de qualquer domínio registrado utilizando:

- Serviços online de consulta WHOIS;
- Ou a ferramenta de linha de comando `whois`, disponível em sistemas Linux (e também pode ser instalada em outros sistemas operacionais).

Como esperado, um registro WHOIS fornece informações detalhadas sobre quem registrou um domínio, incluindo:

- Nome do registrante
- Telefone
- E-mail
- Endereço físico

Além disso, é possível ver **quando o registro foi criado** e **quando foi atualizado pela última vez**.

> 🧾 **Comentário:** Essas informações são úteis para fins legais, verificação de legitimidade, investigações de segurança ou simplesmente para descobrir quem está por trás de um site.

## WHOIS com Proteção de Privacidade

No exemplo abaixo, utilizamos o comando `whois` no terminal para consultar o registro WHOIS de um domínio cujo titular optou por **proteger suas informações pessoais** com um serviço de privacidade.

### Terminal

user@TryHackMe$ whois [REDACTED].com<br>
[...]<br>
Domain Name: [REDACTED].COM<br>
Registry Domain ID: [REDACTED]<br>
Registrar WHOIS Server: whois.godaddy.com<br>
Registrar URL: https://www.godaddy.com<br>
Updated Date: 2017-07-05T16:02:43Z<br>
Creation Date: 1993-04-02T00:00:00Z<br>
Registrar Registration Expiration Date: 2026-10-20T14:56:17Z<br>
Registrar: GoDaddy.com, LLC<br>
Registrar IANA ID: 146<br>
Registrar Abuse Contact Email: abuse@godaddy.com<br>
Registrar Abuse Contact Phone: +1.4806242505<br>
[...]<br>
Registrant Name: Registration Private<br>
Registrant Organization: Domains By Proxy, LLC<br>
Registrant Street: DomainsByProxy.com<br>
[...]<br>


> 🔒 **Comentário:** Neste exemplo, vemos que o nome do registrante está como "Registration Private" e a organização listada é **Domains By Proxy, LLC**, um conhecido serviço de privacidade da GoDaddy. Isso indica que os dados reais da pessoa ou empresa responsável pelo domínio foram **propositalmente ocultados** dos registros públicos WHOIS.

> 💡 **Dica prática:** Essa proteção é útil para indivíduos ou empresas que desejam evitar spam, tentativas de engenharia social ou exposição indevida de dados pessoais.

---

## Conclusão

- WHOIS é uma ferramenta poderosa para identificar quem está por trás de um domínio.
- Porém, **nem todos os registros WHOIS são públicos**: é comum encontrar domínios protegidos por serviços como Domains By Proxy.
- Mesmo quando os dados estão protegidos, ainda é possível encontrar informações relevantes como o **registrador**, **datas de criação e expiração**, e **meios de contato do registrador para denúncias de abuso**.

---
