# Defensive Security Intro

## Introdução

Na Internet, qualquer pessoa pode publicar seus escritos — posts em blogs, artigos, publicações em redes sociais, ou até editar páginas públicas em wikis. Isso permite que alegações sem fundamento circulem livremente.

É nosso papel, como leitores, avaliar essas informações. Aqui estão alguns pontos a considerar:

### Avaliação de Informações

- **Fonte**: Verifique o autor ou a organização. São respeitáveis? Têm autoridade no assunto?
- **Evidência e raciocínio**: Há fatos concretos e argumentos sólidos?
- **Objetividade e viés**: A informação é imparcial? Considera múltiplas perspectivas?
- **Corroboração e consistência**: A informação é confirmada por outras fontes confiáveis?

---

## Mecanismos de Busca

### Operadores de Busca no Google

- `"frase exata"`: Busca páginas com a frase exata. Ex: `"passive reconnaissance"`
- `site:`: Limita a busca a um domínio. Ex: `site:tryhackme.com success stories`
- `-`: Exclui termos. Ex: `pyramids -tourism`
- `filetype:`: Busca por tipo de arquivo. Ex: `filetype:ppt cyber security`

> Consulte a documentação do seu mecanismo de busca favorito para outros operadores avançados.

---

## Mecanismos de Busca Especializados

### Shodan

- Busca dispositivos conectados à Internet.
- Ex: Buscar `apache 2.4.1` para encontrar servidores com essa versão.
- [Shodan Search Query Examples](https://www.shodan.io/search/help)
- [Shodan Trends](https://trends.shodan.io) (requer assinatura)

### Censys

- Foco em hosts, sites, certificados e ativos de rede.
- Casos de uso:
  - Enumerar domínios
  - Auditar portas abertas
  - Descobrir ativos não autorizados
- [Censys Use Cases](https://censys.io)

### VirusTotal

- Escaneia arquivos e URLs com múltiplos antivírus.
- Permite verificar hashes.
- Inclui comentários da comunidade para contextos adicionais.
- [VirusTotal](https://www.virustotal.com)

### Have I Been Pwned

- Verifica se seu e-mail apareceu em vazamentos de dados.
- [Have I Been Pwned](https://haveibeenpwned.com)

---

## Vulnerabilidades e Exploração

### CVE (Common Vulnerabilities and Exposures)

- Dicionário padronizado de vulnerabilidades.
- Ex: `CVE-2024-29988`
- Mantido pela MITRE.
- [CVE Program](https://www.cve.org)
- [National Vulnerability Database](https://nvd.nist.gov)

### Exploit Database

- Repositório de códigos de exploit.
- Muitos são verificados/testados.
- [Exploit DB](https://www.exploit-db.com)

---

## Documentação Técnica

### Linux Manual Pages (man pages)

- Ajuda oficial de comandos Linux/Unix.
- Ex: `man ip` no terminal.
- Também acessível via motores de busca com: `man ip`

### Documentação de Produtos

- Fonte oficial e confiável de informações.
- Exemplos:
  - [Snort Documentation](https://docs.snort.org)
  - [Apache HTTP Server](https://httpd.apache.org/docs/)
  - [PHP Documentation](https://www.php.net/docs.php)
  - [Node.js Docs](https://nodejs.org/en/docs/)

---

> **Dica**: Sempre que possível, consulte a documentação oficial. É a fonte mais atualizada e completa.
