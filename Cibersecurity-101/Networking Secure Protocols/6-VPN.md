# Rede Virtual Privada (VPN)

Considere uma empresa com escritórios em diferentes locais geográficos. Essa empresa pode conectar todos os seus escritórios e locais à matriz principal para que qualquer dispositivo possa acessar os recursos compartilhados como se estivesse fisicamente localizado na matriz? **A resposta é sim**; além disso, a solução mais econômica seria configurar uma **rede virtual privada (VPN)** usando a infraestrutura da Internet. O foco aqui está no **V de Virtual** em VPN.

## A Internet e a Privacidade

Quando a Internet foi projetada, o conjunto de protocolos TCP/IP se concentrou na entrega de pacotes. 

Por exemplo, se um roteador ficar fora de serviço, os protocolos de roteamento podem se adaptar e escolher uma rota diferente para enviar seus pacotes. 

Se um pacote não for reconhecido, o TCP possui mecanismos incorporados para detectar essa situação e reenviar. **No entanto, não há mecanismos implementados para garantir que todos os dados que saem ou entram em um computador estejam protegidos contra divulgação e alteração.** Uma solução popular foi a configuração de uma conexão VPN. O foco aqui está no **P de Privada** em VPN.

## Solução econômica e segura

Quase todas as empresas exigem **troca de informações "privadas"** em sua rede virtual. Assim, uma VPN fornece uma solução muito conveniente e relativamente barata. Os principais requisitos são:

- conectividade com a Internet  
- um servidor VPN  
- um cliente VPN  

---

## Como funciona uma VPN

O **diagrama de rede abaixo** mostra um exemplo de uma empresa com duas filiais remotas conectando-se à matriz. 

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/VPN.png)

Um **cliente VPN nas filiais remotas** é esperado para se conectar ao **servidor VPN na matriz**. 

Nesse caso, o cliente VPN irá **criptografar o tráfego** e passá-lo para a matriz via o **túnel VPN estabelecido** (mostrado em azul). O tráfego da VPN é limitado às **linhas azuis**; as **linhas verdes** transportariam o tráfego VPN descriptografado.

No **diagrama de rede abaixo**, vemos dois usuários remotos usando clientes VPN para se conectar ao servidor VPN na matriz. Nesse caso, o cliente VPN conecta um único dispositivo.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/VPN-2.png)

## O que acontece depois de conectado

Uma vez que um **túnel VPN** é estabelecido, **todo o nosso tráfego da Internet** geralmente será **roteado pela conexão VPN**, i.e. via o túnel VPN. Consequentemente, quando tentarmos acessar um serviço de Internet ou aplicação web, eles **não verão nosso endereço IP público**, mas sim o **do servidor VPN**. 

> Isso é por que alguns usuários da Internet se conectam via VPN para **contornar restrições geográficas**. 

Além disso, o **provedor local de Internet (ISP)** verá apenas **tráfego criptografado**, o que **limita sua capacidade de censurar o acesso à Internet**.

---

## Exemplo prático

Em outras palavras, se um usuário se conecta a um **servidor VPN no Japão**, eles parecerão para os servidores que acessam como se estivessem **localizados no Japão**. Esses servidores personalizarão sua experiência de acordo, como redirecionando-o para a versão japonesa do serviço. 

> A captura de tela abaixo mostra a página de busca do Google após conectar-se a um servidor VPN no Japão.

![alt text](/Cibersecurity-101/Networking%20Secure%20Protocols/IMAGENS/VPN-3.png)

## Nem toda VPN roteia tudo

Embora em muitos cenários, uma pessoa estabeleça uma conexão VPN para **rotear todo o tráfego** pelo túnel VPN, **algumas conexões VPN não fazem isso**.

- O servidor VPN pode ser configurado para **fornecer acesso a uma rede privada**, mas **não para rotear seu tráfego**.
- Além disso, **alguns servidores VPN vazam seu endereço IP real**, embora se espere que eles roteiem todo o seu tráfego pela VPN.

> Dependendo do motivo pelo qual você está usando uma conexão VPN, pode ser necessário executar mais alguns testes, como um **teste de vazamento de DNS (DNS leak test).**

---

## Aviso legal

Finalmente, **alguns países consideram o uso de VPNs ilegal e até punível**. 
**Por favor, verifique as leis e regulamentos locais antes de usar VPNs**, especialmente ao viajar.
