# Topologias de Redes Locais (LAN)

Ao longo dos anos, houve experimentações e implementações de diversos designs de redes. Quando usamos o termo **topologia**, estamos nos referindo ao **design ou aparência da rede**.

## 🌟 Topologia em Estrela

Os dispositivos estão conectados individualmente a um **dispositivo central de rede**, como um switch ou hub.

### ✅ Vantagens
- Maior escalabilidade: fácil adicionar novos dispositivos.
- Alta confiabilidade.
- Fácil de manter com equipamentos de qualidade.

### ❌ Desvantagens
- Custo mais alto (mais cabos e equipamentos).
- Dependência do hardware central: se ele falhar, a rede para.
- Crescimento demanda mais manutenção.

---

## 🚌 Topologia em Barramento (Bus)

Usa uma única conexão principal, chamada **cabo backbone**, com os dispositivos conectados ao longo dela.

### ✅ Vantagens
- Custo baixo: menos cabos e equipamentos.
- Fácil de implementar.

### ❌ Desvantagens
- Gargalos de tráfego.
- Difícil solução de problemas.
- Um único ponto de falha compromete toda a rede.

---

## 🔁 Topologia em Anel

Os dispositivos formam um **laço contínuo**, com pouco cabeamento e sem necessidade de muito hardware.

### ✅ Vantagens
- Fácil detecção de falhas.
- Menos propensa a gargalos.

### ❌ Desvantagens
- Não é eficiente no tráfego de dados.
- Falhas em um dispositivo ou cabo quebram toda a rede.

---

## 🔌 O que é um Switch?

Um switch conecta vários dispositivos em uma rede local. Ele é mais eficiente que um hub porque **encaminha pacotes apenas para o destino correto**.

- Pode ter 4, 8, 16, 24, 32 ou 64 portas.
- Reduz o tráfego desnecessário na rede.
- Conecta-se a roteadores para oferecer caminhos redundantes.

---

## 🌐 O que é um Roteador?

Um roteador **conecta redes diferentes** e permite a comunicação entre elas.

- Usa **roteamento** para encontrar o melhor caminho.
- Essencial para comunicação entre redes internas e a internet.

---

## 🧠 Subrede (Subnetting)

Permite **dividir uma rede maior em redes menores** (sub-redes).

### Benefícios:
- Eficiência.
- Segurança.
- Controle.

### Exemplo prático:
Uma empresa pode dividir a rede em sub-redes como:
- Contabilidade
- RH
- Finanças

### Tipos de Endereços IP:
| Tipo                | Propósito                                   | Exemplo           |
|---------------------|---------------------------------------------|-------------------|
| Endereço de Rede    | Identifica o início da rede                 | 192.168.1.0       |
| Endereço de Host    | Identifica um dispositivo na sub-rede       | 192.168.1.100     |
| Gateway Padrão      | Envia dados para fora da rede local         | 192.168.1.254     |

---

## 🧭 ARP (Address Resolution Protocol)

Permite que um dispositivo associe **endereços IP aos endereços MAC** na rede.

### Funcionamento:
1. Dispositivo envia uma **solicitação ARP**: "Quem tem o IP 192.168.1.100?"
2. O dono do IP responde com seu **endereço MAC**.
3. A informação é armazenada no **cache ARP** para consultas futuras.

---

## 📦 DHCP (Dynamic Host Configuration Protocol)

Protocolo que **atribui IPs automaticamente** na rede.

### Processo:
1. **DHCP Discover**: dispositivo pergunta se há um servidor DHCP.
2. **DHCP Offer**: servidor oferece um IP.
3. **DHCP Request**: dispositivo aceita.
4. **DHCP ACK**: servidor confirma.

---