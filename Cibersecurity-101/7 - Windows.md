# FUNDAMENTOS DO WINDOWS

## Funcionalidades do Windows
### 🖥️ 1. The Desktop (Área de Trabalho)
É a tela principal do Windows após o login. É responsável por:
- Permitir acesso rápido a atalhos de arquivos, pastas e programas.
- Conter widgets (como relógio, clima) e a lixeira.
- Personalizar a área de trabalho (plano de fundo, organização de ícones etc.).

### 🪟 2. Start Menu (Menu Iniciar)
Localizado no canto inferior esquerdo.
Acesso a:
- Programas instalados
- Configurações do sistema
- Botão de desligar/reiniciar
- Aplicativos fixos

É o centro de controle para abrir o que você precisa no sistema.

### 🔍 3. Search Box (Caixa de Pesquisa/Cortana)
Permite pesquisar arquivos, aplicativos e configurações rapidamente. Pode estar associada à Cortana, a assistente virtual do Windows (em versões anteriores).

Exemplo: digitar "bloco de notas" ou "wifi" para abrir rapidamente esses recursos.

### 🗂️ 4. Task View (Visão de Tarefas)
Atalho: Tecla Windows + Tab
Permite:
- Ver todas as janelas abertas no momento
- Criar e alternar entre áreas de trabalho virtuais

Útil para organizar o trabalho em diferentes contextos (ex: estudo, navegação, trabalho).

### 📌 5. Taskbar (Barra de Tarefas)
Linha na parte inferior da tela (por padrão).
Exibe:
- Ícones dos programas em uso ou fixados
- Botão do menu iniciar
- Caixa de pesquisa
- Área de notificações

Também mostra janelas minimizadas e permite alternar entre apps rapidamente.

### 🔧 6. Toolbars (Barras de Ferramentas)
São componentes adicionais que você pode ativar na barra de tarefas.
Exemplos:
- Barra de endereços
- Barra de links (atalhos para sites)
- Barra de pastas

Facilitam o acesso direto a recursos frequentemente usados.

### 🔔 7. Notification Area (Área de Notificação)
Fica à direita da barra de tarefas.
Mostra:
- Relógio e data
- Ícones de sistema (volume, rede, bateria)
- Alertas de segurança, atualizações, notificações de apps

A central de ações (ícone de balão) também aparece aqui.

## Sistema de Arquivos do Windows

### 🧾 O que é um sistema de arquivos?
É a forma como o sistema operacional organiza, armazena e recupera dados no disco.

### ⚙️ NTFS (New Technology File System)
É o sistema de arquivos usado por padrão em versões modernas do Windows (XP em diante). Foi criado para substituir sistemas antigos como FAT16, FAT32 e HPFS.

NTFS é um sistema com recursos avançados de segurança, confiabilidade e desempenho.

#### 🆚 Comparando com FAT
| Característica                     | FAT16/FAT32                 | NTFS                          |
|-----------------------------------|-----------------------------|-------------------------------|
| Suporte a arquivos grandes        | ❌ (limite de 4GB)          | ✅ (acima de 4GB)             |
| Permissões e segurança            | ❌                          | ✅ (Controle de Acesso - ACL) |
| Compressão de arquivos            | ❌                          | ✅                            |
| Criptografia                      | ❌                          | ✅ (EFS)                      |
| Recuperação de erros (journaling) | ❌                          | ✅                            |

#### 📦 NTFS é um sistema de arquivos com journaling
Significa que ele registra operações em um log interno. Se houver uma falha (ex: queda de energia), ele pode usar esse log para reparar automaticamente os arquivos.

#### 🧠 Outras vantagens do NTFS:
- Compactação de arquivos e pastas para economizar espaço. 
- Criptografia com EFS (Encrypting File System) – protege dados contra acesso não autorizado.
- Controle de permissões avançadas para segurança de arquivos.
- Suporte a longos nomes de arquivos e muitos arquivos por pasta.

#### 💾 E o FAT ainda existe?
Sim! Mas geralmente em dispositivos removíveis:
- Pen drives
- Cartões SD
- Câmeras digitais

É usado porque é mais compatível com outros sistemas operacionais (Linux, macOS, TVs etc.).

### 🔍 Como saber qual sistema de arquivos meu Windows usa?
Abra o Explorador de Arquivos. Clique com o botão direito no disco C:\ (onde o Windows está instalado). Vá em "Propriedades". Veja a informação em "Sistema de arquivos" (deve aparecer “NTFS”).

## Permissões Específicas do NTFS

O sistema de arquivos **NTFS (New Technology File System)**, utilizado nas versões modernas do Windows, oferece recursos avançados de segurança que não estão disponíveis em sistemas como FAT16/FAT32.

Um desses recursos é a capacidade de definir **permissões de acesso** a arquivos e pastas. Essas permissões permitem **conceder ou negar** o acesso a usuários e grupos específicos, garantindo maior controle sobre os dados armazenados.

### Permissões Disponíveis no NTFS

As principais permissões que podem ser atribuídas a arquivos e pastas em volumes NTFS são:

- ✅ **Full Control (Controle Total)**  
  Permite realizar qualquer ação no arquivo ou pasta, incluindo leitura, escrita, modificação, exclusão e alteração de permissões.

- ✏️ **Modify (Modificar)**  
  Permite ler, escrever e excluir o conteúdo, mas não alterar permissões ou assumir a propriedade.

- 🔍 **Read & Execute (Ler e Executar)**  
  Permite visualizar o conteúdo e executar arquivos (como programas ou scripts).

- 📂 **List Folder Contents (Listar Conteúdo da Pasta)**  
  Permite ver os arquivos e subpastas dentro de uma pasta (aplicável apenas a pastas).

- 📖 **Read (Ler)**  
  Permite abrir e visualizar o conteúdo do arquivo ou pasta, mas sem alterar nada.

- 📝 **Write (Escrever)**  
  Permite modificar o conteúdo e criar novos arquivos ou pastas, mas sem apagar os existentes.

Essas permissões são configuradas através do sistema de **Controle de Acesso (Access Control List - ACL)** do Windows, que oferece um gerenciamento refinado e seguro dos recursos do sistema.

## Alternate Data Streams (ADS)

Outra funcionalidade importante do **NTFS** é o suporte a **Alternate Data Streams (ADS)**.

### O que são ADS?

**Alternate Data Streams** são atributos de arquivos específicos do sistema de arquivos **NTFS**, permitindo que um arquivo possua **mais de um fluxo de dados**.

Por padrão, **todo arquivo no NTFS possui pelo menos um fluxo de dados**, chamado `$DATA`. Com ADS, é possível adicionar **fluxos adicionais** ao mesmo arquivo, sem que eles sejam visíveis no **Windows Explorer**.

### Características do ADS

- O conteúdo adicional armazenado nos ADS **não aparece normalmente no sistema de arquivos**, o que pode ser usado tanto para fins legítimos quanto maliciosos.
- **PowerShell** pode ser usado para visualizar esses fluxos alternativos, enquanto o Windows Explorer não exibe nativamente essa informação.
- Alguns **programas de terceiros** também permitem visualizar ADS de forma mais prática.

### ADS e Segurança

- 🛡️ **Uso malicioso:** autores de malware podem usar ADS para **ocultar código malicioso** ou arquivos, dificultando sua detecção por usuários e antivírus tradicionais.
- ✅ **Uso legítimo:** arquivos baixados da Internet, por exemplo, recebem **informações extras nos ADS** que indicam sua origem (Internet Zone Identifier).

### Exemplo prático

Para verificar os fluxos alternativos de um arquivo usando PowerShell:

```powershell
Get-Item -Path .\arquivo.txt -Stream *
