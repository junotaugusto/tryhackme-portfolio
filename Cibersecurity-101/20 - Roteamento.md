# 🌐 Roteamento na Internet

Considere o diagrama de rede mostrado abaixo. Ele possui apenas três redes; no entanto, como a Internet consegue descobrir como entregar um pacote da **Rede 1** para a **Rede 2** ou **Rede 3**? Apesar de ser um diagrama simplificado, precisamos de algum algoritmo que descubra como conectar a Rede 1 às outras redes — e vice-versa.

*️⃣ *Mesmo em uma rede pequena, precisamos de lógica para saber por onde enviar os pacotes. Imagine o desafio em escala global!*

![alt text](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1719849271800.svg)


Vamos considerar um diagrama mais detalhado. A Internet seria composta por **milhões de roteadores** e **bilhões de dispositivos**. A rede abaixo é apenas um subconjunto minúsculo da Internet. O usuário móvel consegue alcançar o servidor web; no entanto, para que isso ocorra, **cada roteador no caminho precisa enviar os pacotes pelo link apropriado**.

*️⃣ *Os roteadores precisam tomar decisões autônomas sobre o melhor caminho para cada pacote. Por isso, precisam de algoritmos de roteamento.*

Obviamente, existe **mais de um caminho** (ou rota) conectando o usuário móvel ao servidor web. Por isso, é necessário **um algoritmo de roteamento** para que o roteador descubra qual link usar.

*️⃣ *Mais de um caminho significa mais de uma escolha — e é aí que entram os algoritmos: para escolher a rota ideal com base em critérios como velocidade, custo ou distância.*

![alt text](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1719849333579.svg)

## 🧠 Algoritmos e Protocolos de Roteamento

Os algoritmos de roteamento são complexos e vão além do escopo desta introdução. No entanto, é importante conhecer os principais **protocolos de roteamento**, pois eles são fundamentais para o funcionamento da Internet.

*️⃣ *Esses protocolos são como "regras de navegação" para os roteadores. Cada um tem sua lógica e aplicação ideal.*

---

### 📌 OSPF (Open Shortest Path First)

O **OSPF** é um protocolo de roteamento que permite que roteadores compartilhem informações sobre a topologia da rede e calculem os caminhos mais eficientes para a transmissão de dados.

- Os roteadores trocam atualizações sobre o estado de seus links e redes conectadas.
- Cada roteador constrói um **mapa completo da rede** e consegue determinar as melhores rotas para qualquer destino.

*️⃣ *O OSPF é muito usado em redes corporativas e funciona como um GPS interno entre roteadores — ele sempre tenta achar o caminho mais curto.*

---

### 📌 EIGRP (Enhanced Interior Gateway Routing Protocol)

O **EIGRP** é um protocolo proprietário da Cisco que combina aspectos de diferentes algoritmos de roteamento.

- Os roteadores compartilham informações sobre as redes que podem alcançar e os custos dessas rotas (como largura de banda e atraso).
- A partir disso, os roteadores escolhem os caminhos mais eficientes para enviar os dados.

*️⃣ *Mais inteligente que o RIP e mais leve que o OSPF, o EIGRP foi criado para equilibrar eficiência com simplicidade, mas só funciona em equipamentos Cisco.*

---

### 📌 BGP (Border Gateway Protocol)

O **BGP** é o principal protocolo de roteamento utilizado na Internet.

- Ele permite que diferentes redes (como os provedores de Internet) troquem informações de roteamento.
- O BGP estabelece os caminhos pelos quais os dados devem transitar entre redes distintas.
- Ele garante que os pacotes sejam roteados de forma eficiente mesmo ao atravessar **múltiplas redes**.

*️⃣ *O BGP é o "Waze" da Internet global — é com ele que as grandes redes (como Google, Vivo, Claro, etc.) decidem por onde os pacotes devem passar.*

---

### 📌 RIP (Routing Information Protocol)

O **RIP** é um protocolo de roteamento simples, geralmente utilizado em redes pequenas.

- Os roteadores que usam RIP compartilham informações sobre as redes que podem alcançar e o número de **hops** (saltos/roteadores) até lá.
- Com base nisso, cada roteador constrói sua **tabela de roteamento**, escolhendo os caminhos com **menos saltos**.

*️⃣ *Apesar de antigo e limitado (só aceita até 15 saltos), o RIP ainda é útil para fins educacionais e em redes pequenas.*

---
