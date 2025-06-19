# TLS – Transport Layer Security

Em determinado momento, bastava uma ferramenta de captura de pacotes para ler todos os chats, e-mails e senhas dos usuários em sua rede. Não era incomum que um invasor colocasse sua placa de rede em **modo promíscuo**, ou seja, para capturar todos os pacotes, inclusive aqueles que não eram destinados a ela. 

Posteriormente, ele examinava todas as capturas de pacotes e obtinha as credenciais de login de vítimas desavisadas. Não havia nada que um usuário pudesse fazer para impedir que sua senha de login fosse enviada em texto claro. Hoje em dia, tornou-se incomum encontrar um serviço que envie credenciais de login em texto claro.

No início dos anos 1990, a **Netscape Communications** reconheceu a necessidade de comunicação segura na World Wide Web. Eventualmente, eles desenvolveram o **SSL (Secure Sockets Layer)** e lançaram o **SSL 2.0** em 1995 como a primeira versão pública. Em 1999, a **Internet Engineering Task Force (IETF)** desenvolveu o **TLS (Transport Layer Security)**. 

Embora muito semelhante, o **TLS 1.0** foi uma atualização do **SSL 3.0** e ofereceu várias melhorias de segurança. Em 2018, o TLS passou por uma reformulação significativa e o **TLS 1.3** foi lançado. 

O objetivo aqui não é lembrar as datas exatas, mas perceber a quantidade de trabalho e tempo investidos no desenvolvimento da versão atual do TLS, ou seja, o **TLS 1.3**. Ao longo de mais de duas décadas, houve muito o que aprender e melhorar em cada versão.

Assim como o SSL, seu predecessor, o TLS é um **protocolo criptográfico que opera na camada de transporte** do modelo OSI. Ele permite a comunicação segura entre um cliente e um servidor através de uma rede insegura. Por **segura**, referimo-nos à **confidencialidade e integridade**; o TLS garante que ninguém possa ler ou modificar os dados trocados. 

Reserve um minuto para pensar em como seria fazer compras online, transações bancárias, ou mesmo mensagens e e-mails sem poder garantir a confidencialidade e integridade dos pacotes de rede. Sem o TLS, não poderíamos usar a Internet para muitas aplicações que hoje fazem parte da nossa rotina diária.

Hoje em dia, dezenas de protocolos receberam atualizações de segurança com a simples adição do TLS. Exemplos incluem **HTTP, DNS, MQTT e SIP**, que se tornaram **HTTPS, DoT (DNS over TLS), MQTTS e SIPS**, onde o “S” adicionado significa **Secure** devido ao uso de **SSL/TLS**. Nas tarefas a seguir, visitaremos **HTTPS, SMTPS, POP3S e IMAPS**.

---

## Fundamentos Técnicos

Não discutiremos o **handshake do TLS** aqui; no entanto, se você estiver curioso, pode consultar a sala **Network Security Protocols**. Daremos uma visão geral de como o TLS é configurado e usado.

O primeiro passo para qualquer servidor (ou cliente) que precisa se identificar é obter um **certificado TLS assinado**. Em geral, o administrador do servidor cria uma **CSR (Certificate Signing Request)** e a envia para uma **Autoridade Certificadora (CA)**; a CA verifica a CSR e emite um **certificado digital**. 

Uma vez que o certificado (assinado) é recebido, ele pode ser usado para identificar o servidor (ou o cliente) para terceiros, que poderão confirmar a validade da assinatura. Para que um host confirme a validade de um certificado assinado, os **certificados das autoridades certificadoras** precisam estar instalados no host. 

No mundo não digital, isso é semelhante a reconhecer os carimbos de várias autoridades. A captura de tela abaixo mostra as autoridades confiáveis instaladas em um navegador da web.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/certificate.png)

> **Autoridades certificadoras instaladas por padrão em um navegador web**

De modo geral, obter um certificado assinado requer o **pagamento de uma taxa anual**. No entanto, o **Let’s Encrypt** permite que você obtenha seu certificado assinado **gratuitamente**.

Por fim, vale mencionar que alguns usuários optam por criar um **certificado autoassinado**. Um certificado autoassinado **não pode comprovar a autenticidade do servidor**, pois nenhuma terceira parte confiável confirmou sua validade.
