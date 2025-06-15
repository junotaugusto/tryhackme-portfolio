## Protocolo ICMP

O **ICMP (Internet Control Message Protocol)** é usado principalmente para **diagnósticos de rede** e **relatórios de erro**. Dois comandos muito populares dependem do ICMP e são extremamente úteis tanto para a **resolução de problemas de rede** quanto para a **segurança de redes**. Esses comandos são:

- **ping**: Esse comando usa o ICMP para testar a conectividade com um sistema de destino e medir o tempo de ida e volta (**RTT – Round-Trip Time**). Em outras palavras, pode ser usado para verificar se o destino está ativo e se a resposta dele consegue alcançar o nosso sistema.

- **traceroute**: Esse comando se chama `traceroute` em sistemas Linux e Unix-like, e `tracert` em sistemas Microsoft Windows. Ele utiliza ICMP para descobrir o **caminho que os pacotes percorrem** do seu host até o destino.

---

## Ping

Você pode nunca ter jogado ping-pong antes (tênis de mesa); no entanto, graças ao ICMP, agora você pode jogar com o computador! O comando `ping` envia uma **ICMP Echo Request** (**ICMP Tipo 8**).

A imagem abaixo mostra a mensagem ICMP encapsulada dentro de um pacote IP.
![alt text](image-1.png)

O computador que recebe a mensagem responde com uma **ICMP Echo Replay**(**ICMP Tipo 0**).

![alt text](image-2.png)

## Possíveis Falhas ao Usar o Ping

Muitas coisas podem impedir que recebamos uma resposta ao usar o `ping`. Além da possibilidade do **sistema de destino estar offline ou desligado**, um **firewall ao longo do caminho pode bloquear os pacotes necessários** para que o ping funcione.

No exemplo abaixo, usamos o parâmetro `-c 4` para dizer ao comando `ping` que pare após o envio de **quatro pacotes**.

### Terminal

user@TryHackMe$ ping 192.168.11.1 -c 4  <br>
PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.  <br>
64 bytes from 192.168.11.1: icmp_seq=1 ttl=63 time=11.2 ms  <br>
64 bytes from 192.168.11.1: icmp_seq=2 ttl=63 time=3.81 ms  <br>
64 bytes from 192.168.11.1: icmp_seq=3 ttl=63 time=3.99 ms  <br>
64 bytes from 192.168.11.1: icmp_seq=4 ttl=63 time=23.4 ms  <br>

--- 192.168.11.1 ping statistics ---  <br>
4 packets transmitted, 4 received, 0% packet loss, time 3003ms  <br>
rtt min/avg/max/mdev = 3.805/10.596/23.366/7.956 ms  <br>

---

A saída mostra que **não houve perda de pacotes**. Além disso, o comando `ping` calcula o **tempo de ida e volta (RTT)** em quatro métricas:

- **mínimo (min)**
- **média (avg)**
- **máximo (max)**
- **desvio padrão (mdev)**

Esses valores ajudam a **avaliar a qualidade da conexão** com o host de destino.

---

*🔹 `icmp_seq` indica o número sequencial do pacote ICMP enviado. É útil para identificar se houve perda de pacotes ou alteração na ordem de chegada.*  
*🔹 `ttl` (time to live) representa o número máximo de saltos (hops) que o pacote pode dar até ser descartado. Cada roteador decrementa esse valor em 1. Isso ajuda a evitar loops infinitos na rede.*  
*🔹 Um firewall pode estar configurado para bloquear pacotes ICMP por questões de segurança, impedindo o funcionamento do ping, mesmo que o host esteja online.*  
