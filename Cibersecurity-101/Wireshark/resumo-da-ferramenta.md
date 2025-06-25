# Casos de Uso

O Wireshark é uma das ferramentas de análise de tráfego mais poderosas disponíveis. Há múltiplos propósitos para seu uso:

- Detectar e solucionar problemas de rede, como pontos de falha de carga de rede e congestionamento.
- Detectar anomalias de segurança, como hosts maliciosos, uso anormal de portas e tráfego suspeito.
- Investigar e aprender detalhes de protocolos, como códigos de resposta e dados de carga útil.

> **Nota:** O Wireshark não é um Sistema de Detecção de Intrusão (IDS). Ele apenas permite que analistas descubram e investiguem pacotes em profundidade. Ele também não modifica pacotes; ele apenas os lê. Portanto, detectar qualquer anomalia ou problema de rede depende fortemente do conhecimento e das habilidades de investigação do analista.

---

# GUI e Dados

A interface gráfica do Wireshark se abre com uma única página integrada, que ajuda os usuários a investigar o tráfego de múltiplas formas. À primeira vista, cinco seções se destacam:

| **Seção**                     | **Descrição** |
|------------------------------|---------------|
| **Barra de Ferramentas**     | A barra principal contém múltiplos menus e atalhos para captura e processamento de pacotes, incluindo filtragem, ordenação, resumo, exportação e mesclagem. |
| **Barra de Filtro de Exibição** | A seção principal de consulta e filtragem. |
| **Arquivos Recentes**        | Lista dos arquivos investigados recentemente. Você pode reabrir os arquivos listados com um duplo clique. |
| **Filtros de Captura e Interfaces** | Filtros de captura e pontos de escuta disponíveis (interfaces de rede). A interface de rede é o ponto de conexão entre um computador e uma rede. A conexão de software (por exemplo, `lo`, `eth0` e `ens33`) habilita o hardware de rede. |
| **Barra de Status**          | Status da ferramenta, perfil e informações numéricas dos pacotes. |

A imagem abaixo mostra a janela principal do Wireshark. As seções explicadas na tabela estão destacadas. Agora abra o Wireshark e siga o guia passo a passo.

![alt text](/Cibersecurity-101/Wireshark/IMAGENS/ferramenta-1.png)

# Carregando Arquivos PCAP

A imagem acima mostra a interface vazia do Wireshark. A única informação disponível é o arquivo recentemente processado “http1.cap”. 

Vamos carregar esse arquivo e ver a apresentação detalhada de pacotes do Wireshark. Observe que você também pode usar o menu “Arquivo”, arrastar e soltar o arquivo ou clicar duas vezes sobre ele para carregar um pcap.

 ![alt text](/Cibersecurity-101/Wireshark/IMAGENS/ferramenta-2.png)

Agora, podemos ver o nome do arquivo processado, o número detalhado de pacotes e os detalhes dos pacotes. Os detalhes dos pacotes são exibidos em três painéis diferentes, o que nos permite explorá-los em formatos distintos.

### Painel de Lista de Pacotes  
Resumo de cada pacote (endereços de origem e destino, protocolo e informações do pacote). Você pode clicar na lista para escolher um pacote para investigação adicional. Uma vez selecionado, os detalhes aparecerão nos outros painéis.

### Painel de Detalhes do Pacote  
Detalhamento do protocolo do pacote selecionado.

### Painel de Bytes do Pacote  
Representação em hexadecimal e ASCII decodificado do pacote selecionado. Ele destaca o campo do pacote dependendo da seção clicada no painel de detalhes.

---

# Colorindo Pacotes

Junto com as informações rápidas dos pacotes, o Wireshark também colore pacotes de acordo com diferentes condições e protocolos para identificar rapidamente anomalias e protocolos nas capturas (isso explica por que quase tudo está verde nas capturas de tela fornecidas). 

Esse panorama das informações dos pacotes pode ajudar a rastrear exatamente o que você está procurando durante a análise. Você pode criar regras de coloração personalizadas para identificar eventos de interesse usando filtros de exibição, que abordaremos no próximo room. 

Agora, vamos focar nos padrões e entender como visualizar e usar os detalhes de dados representados.

O Wireshark possui dois tipos de métodos de coloração de pacotes:  
**1 - Regras Temporárias:** Estão disponíveis apenas durante uma sessão do programa.

**2 - Regras Permanentes:** São salvas no arquivo de preferências (perfil) e disponíveis para a próxima sessão do programa.

Você pode usar o “menu do botão direito” ou o menu **“Exibir → Regras de Coloração”** para criar regras de coloração permanentes. 

O menu **“Colorir Lista de Pacotes”** ativa/desativa as regras de coloração.  A coloração temporária de pacotes é feita com o “menu do botão direito” ou o menu **“Exibir → Filtro de Conversa”**, que será abordado na TAREFA-5.

A coloração permanente padrão é mostrada abaixo.

![alt text](/Cibersecurity-101/Wireshark/IMAGENS/ferramenta-3.png)


