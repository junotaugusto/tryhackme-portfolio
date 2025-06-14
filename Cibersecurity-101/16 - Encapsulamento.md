## Encapsulation

Antes de concluir, é fundamental explicar outro conceito-chave: **encapsulamento**.

Neste contexto, **encapsulamento** refere-se ao processo em que **cada camada adiciona um cabeçalho (e, às vezes, um rodapé)** à unidade de dados recebida e envia essa unidade “encapsulada” para a camada inferior.

Esse conceito é essencial porque **permite que cada camada se concentre exclusivamente em sua função**. Na imagem abaixo, temos as seguintes quatro etapas: *(inserir aqui)*.

O processo precisa ser **invertido no lado do receptor**, até que os dados da aplicação sejam extraídos.

---

## A Vida de um Pacote (The Life of a Packet)

Com base no que estudamos até agora, podemos descrever uma versão simplificada da vida de um pacote. Vamos considerar o cenário em que você realiza uma busca por uma sala no site TryHackMe:

1. Na página de busca do TryHackMe, você digita sua consulta e pressiona Enter.
2. Seu navegador, usando HTTPS, prepara uma requisição HTTP e a envia para a camada inferior: a **camada de transporte**.
3. A camada **TCP** estabelece uma conexão via **three-way handshake** entre seu navegador e o servidor do TryHackMe. Após isso, pode enviar a requisição HTTP com sua busca. Cada segmento TCP criado é repassado à camada inferior: a **camada de Internet**.
4. A camada **IP** adiciona o endereço IP de origem (seu computador) e o de destino (servidor TryHackMe). Para alcançar o roteador, seu laptop entrega esse pacote à camada inferior: a **camada de enlace**.
5. A **camada de enlace** (Ethernet ou WiFi) adiciona o cabeçalho e o rodapé adequados, e o pacote é enviado ao roteador.
6. O roteador remove o cabeçalho e rodapé da camada de enlace, inspeciona o endereço IP de destino e roteia o pacote para o próximo salto. Cada roteador repete esse processo até alcançar o roteador do servidor de destino.
7. Os passos então são **revertidos** à medida que o pacote se aproxima do destino, até que os dados da aplicação sejam extraídos.

---

## Resumo da Jornada do Pacote

- **Dados da aplicação**: Tudo começa quando o usuário insere dados em uma aplicação (por exemplo, escreve um e-mail) e pressiona “enviar”. A aplicação formata esses dados e os envia usando a camada de transporte.
- **Segmento ou datagrama da camada de transporte**: A camada de transporte (como TCP ou UDP) adiciona seu cabeçalho apropriado e cria um segmento TCP (ou datagrama UDP), que é enviado à camada de rede.
- **Pacote de rede**: A camada de rede (camada Internet) adiciona um cabeçalho IP ao segmento recebido e envia o **pacote IP** à camada de enlace.
- **Quadro da camada de enlace**: A Ethernet ou WiFi recebe o pacote IP e adiciona o cabeçalho e o rodapé apropriados, criando um **quadro (frame)**.

🔁 Recomeçamos com os dados da aplicação. Na camada de transporte, adicionamos o cabeçalho TCP ou UDP, criando um segmento ou datagrama. Na camada de rede, adicionamos o cabeçalho IP, formando um pacote IP que pode ser roteado. Por fim, na camada de enlace, adicionamos cabeçalho e rodapé adequados, formando um quadro Ethernet ou WiFi pronto para transmissão.
