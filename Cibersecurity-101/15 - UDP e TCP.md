# Protocolos de Transporte: UDP e TCP

O protocolo IP nos permite alcançar um host de destino na rede; esse host é identificado por seu **endereço IP**. No entanto, precisamos de protocolos que permitam que **processos em hosts diferentes se comuniquem**. Para isso, usamos dois protocolos de transporte: **UDP** e **TCP**.

---

## UDP

**UDP (User Datagram Protocol)** nos permite alcançar um **processo específico** no host de destino. É um protocolo **simples e sem conexão**, que opera na **camada 4 (Transporte)** do modelo OSI.

> “Sem conexão” significa que não é necessário estabelecer uma conexão antes de enviar dados. O UDP **não garante que o pacote será entregue** nem possui mecanismo para saber se ele foi recebido.

Para alcançar o processo correto, utilizamos os **números de porta**. Uma porta usa **dois octetos (16 bits)**, permitindo valores entre **1 e 65535**. A **porta 0 é reservada**.

> ℹ️ 65535 vem da expressão 2¹⁶ - 1 (o valor máximo que dois octetos podem representar).

### Analogia com a vida real:

UDP é como enviar uma carta pelo **correio comum**, sem confirmação de entrega. Não há garantia de que será entregue, mas é **mais barato e rápido**. Com o UDP, temos algo parecido: **sem garantias, mas com mais velocidade**.

---

## TCP

**TCP (Transmission Control Protocol)** é um protocolo de transporte **orientado à conexão**, também operando na **camada 4**. Ele possui **mecanismos que garantem a entrega confiável** dos dados.

> Orientado à conexão significa que é necessário **estabelecer uma conexão** antes de qualquer dado ser enviado.

Cada **octeto (byte) de dados** enviado via TCP tem um **número de sequência**, o que ajuda a identificar pacotes perdidos ou duplicados. O **receptor envia confirmações (ACK)** para indicar que recebeu os dados corretamente, usando um número que representa o último octeto recebido.

### Handshake de três vias (Three-Way Handshake)

Para estabelecer uma conexão TCP, ocorre uma **troca de três pacotes**, utilizando os flags **SYN** (sincronizar) e **ACK** (confirmação):

1. **SYN**: O cliente inicia enviando um pacote SYN com seu número de sequência inicial.
2. **SYN-ACK**: O servidor responde com um pacote que tem os flags SYN e ACK, contendo seu próprio número de sequência.
3. **ACK**: O cliente responde com um pacote ACK, confirmando o recebimento do SYN-ACK.

> ✅ Isso completa a negociação inicial da conexão TCP.

Assim como o UDP, o TCP utiliza **números de porta** para identificar os processos que iniciam ou escutam por conexões. E, novamente, as portas válidas vão de **1 a 65535**, com a **porta 0 reservada**.
