# 🌐 Modelo TCP/IP: Uma Implementação Real

Agora que estudamos o modelo conceitual **ISO/OSI**, é hora de analisar um **modelo implementado de verdade**: o **modelo TCP/IP**.

---

## 🔧 Origem do Modelo TCP/IP

TCP/IP significa **Transmission Control Protocol / Internet Protocol**. Foi desenvolvido **nos anos 1970 pelo Departamento de Defesa dos EUA (DoD)**.

🛡️ **Por quê o DoD criou isso?**

Uma das principais forças do modelo TCP/IP é permitir que **uma rede continue funcionando mesmo que partes dela estejam fora do ar**, como em um **ataque militar**.

🔁 Isso é possível, em parte, graças à forma como os **protocolos de roteamento** foram projetados: eles **se adaptam automaticamente** às mudanças de topologia da rede.

---

## 🔁 Comparando com o Modelo OSI

Enquanto o modelo OSI foi apresentado de **baixo para cima (da camada 1 à 7)**, aqui vamos analisar o modelo TCP/IP de **cima para baixo**.

### 🔷 Camadas do Modelo TCP/IP

| Ordem | Camada TCP/IP         | Equivalente no OSI                | Comentário |
|-------|------------------------|-----------------------------------|------------|
| 1     | **Application Layer**  | Camadas 5 (sessão), 6 (apresentação), e 7 (aplicação) | Tudo consolidado numa única camada |
| 2     | **Transport Layer**    | Camada 4                          | Gerencia a comunicação fim a fim |
| 3     | **Internet Layer**     | Camada 3 (rede)                   | Responsável por endereçamento e roteamento |
| 4     | **Link Layer**         | Camada 2 (enlace)                 | Comunicação entre dispositivos no mesmo meio |
| -     | *(Physical Layer)*     | Camada 1 (física)                 | Às vezes incluída em versões com 5 camadas |

---

## 📚 Exemplo: Correspondência de Camadas OSI e TCP/IP

| Nº OSI | Modelo OSI             | Modelo TCP/IP (RFC 1122) | Protocolos Comuns                           |
|--------|------------------------|---------------------------|---------------------------------------------|
| 7      | Aplicação              | Application Layer         | HTTP, HTTPS, FTP, SMTP, IMAP, Telnet, SSH   |
| 6      | Apresentação           |                           | (Incorporada na camada de Aplicação)        |
| 5      | Sessão                 |                           | (Incorporada na camada de Aplicação)        |
| 4      | Transporte             | Transport Layer           | TCP, UDP                                     |
| 3      | Rede                   | Internet Layer            | IP, ICMP, IPSec                              |
| 2      | Enlace                 | Link Layer                | Ethernet (802.3), WiFi (802.11)              |
| 1      | Física                 | *(nem sempre aparece)*    | Cabos, rádio, sinais ópticos, etc.          |

---

## 📘 Observação Didática

Muitos livros modernos de redes mostram o modelo TCP/IP com **cinco camadas**, incluindo explicitamente a camada física.  
Exemplo: no livro **_Computer Networking: A Top-Down Approach_ (8ª edição)** de **Kurose e Ross**, temos:

1. Application  
2. Transport  
3. Network  
4. Link  
5. Physical

🔎 Essa visão mais prática ajuda a separar melhor as responsabilidades da camada de hardware.

---

## 🔜 O Que Vem a Seguir?

Nos próximos estudos, vamos abordar:
- O protocolo **IP** da camada Internet
- Os protocolos **UDP** e **TCP** da camada de transporte

Esses são **blocos fundamentais** da comunicação na internet moderna.

---

> 🧠 Este material faz parte do caderno digital de estudos de redes e cibersegurança de Junot (TryHackMe - Conceitos de Rede).
