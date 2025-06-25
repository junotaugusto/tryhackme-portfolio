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