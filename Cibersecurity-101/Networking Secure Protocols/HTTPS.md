# HTTP e HTTPS – Tráfego em Texto Claro vs Criptografado

Como estudamos na sala **Networking Core Protocols**, o HTTP depende do protocolo TCP e usa, por padrão, a porta 80. Também vimos como todo o tráfego HTTP era enviado em texto claro, permitindo que qualquer pessoa o interceptasse e monitorasse. 

A captura de tela abaixo, retirada da sala anterior, mostra claramente como um adversário pode facilmente ler todo o tráfego trocado entre o cliente e o servidor.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-1.png)

Vamos reservar um momento para revisar os passos mais comuns antes que um navegador web possa solicitar uma página via HTTP. Após resolver o nome de domínio para um endereço IP, o cliente realizará os seguintes dois passos:

1. Estabelecer o **handshake de três vias do TCP** com o servidor de destino.  
2. Comunicar-se usando o protocolo HTTP; por exemplo, enviar requisições como `GET / HTTP/1.1`.

Os dois passos descritos acima são mostrados na janela abaixo. Os três pacotes do handshake TCP (marcados com **1**) precedem o primeiro pacote HTTP com o comando `GET`. A comunicação HTTP está marcada com **2**. Os últimos três pacotes exibidos são para a **finalização da conexão TCP** e estão marcados com **3**.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-2.png)

## HTTP sobre TLS

**HTTPS** significa *Hypertext Transfer Protocol Secure*. Trata-se, basicamente, de **HTTP sobre TLS**. Consequentemente, solicitar uma página via HTTPS exigirá os seguintes três passos (após resolver o nome de domínio):

1. Estabelecer o handshake TCP de três vias com o servidor de destino  
2. Estabelecer uma **sessão TLS**  
3. Comunicar-se usando o protocolo HTTP; por exemplo, emitir requisições HTTP como `GET / HTTP/1.1`

A captura de tela abaixo mostra que uma sessão TCP é estabelecida nos três primeiros pacotes, marcados com **1**. Em seguida, vários pacotes são trocados para negociar o protocolo TLS, marcados com **2**. Os itens **1 e 2** representam onde ocorre a **negociação e o estabelecimento do TLS**.

Finalmente, os dados da aplicação HTTP são trocados, marcados com **3**. Observando a captura no Wireshark, vemos que ela exibe “Application Data”, pois **não há como saber se é HTTP ou outro protocolo sendo enviado na porta 443**.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-3.png)

## Tentando visualizar os dados criptografados

Como esperado, se tentarmos seguir o fluxo dos pacotes e combinar todo o conteúdo, obteremos apenas **caracteres embaralhados**, como mostrado na imagem abaixo. 

O tráfego trocado está **criptografado**; os dados em vermelho foram enviados pelo cliente e os em azul, pelo servidor. **Não há como saber o conteúdo sem obter a chave de criptografia**.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-4.png)

---

## Obtendo a chave de criptografia

Ao adicionar TLS ao HTTP, todos os pacotes passam a ser criptografados. **Não podemos mais ver o conteúdo dos pacotes trocados**, a menos que tenhamos acesso à chave privada.

Embora seja improvável que tenhamos acesso às chaves usadas em uma sessão TLS real, repetimos as capturas de tela acima após fornecer a **chave de descriptografia ao Wireshark**. 

Os handshakes TCP e TLS não mudam; a principal diferença começa com o protocolo HTTP, marcado com **3**. Por exemplo, podemos ver quando o cliente envia um comando `GET`.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-5.png)

Se você quiser ver os dados trocados, agora é a sua chance! **Ainda é tráfego HTTP comum, apenas escondido de olhos curiosos.**

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/https-6.png)

## Conclusão

O principal aprendizado aqui é que o **TLS oferece segurança para o HTTP sem exigir alterações nos protocolos das camadas inferiores ou superiores**. Em outras palavras, os protocolos **TCP e IP não foram modificados**, enquanto o HTTP foi enviado sobre TLS da mesma forma que seria enviado sobre TCP.
