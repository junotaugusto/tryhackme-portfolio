# 🧩 PowerShell – Sintaxe Básica e Cmdlets

## 📌 Sintaxe Básica: Verbo-Substantivo

Como mencionado anteriormente, os comandos do PowerShell são chamados de **cmdlets** (lê-se "command-lets"). Eles são muito mais poderosos do que os comandos tradicionais do Windows e permitem manipulação avançada de dados.

Os **cmdlets** seguem uma convenção de nomenclatura consistente no formato **Verbo-Substantivo**. Essa estrutura facilita a compreensão do que cada cmdlet faz.

- O **Verbo** descreve a ação.
- O **Substantivo** especifica o objeto sobre o qual a ação será executada.

### Exemplos:
- `Get-Content`: Recupera (get) o conteúdo de um arquivo e exibe no console.
- `Set-Location`: Altera (set) o diretório de trabalho atual.

---

## ⚙️ Cmdlets Básicos

### 🔎 `Get-Command`

Lista todos os **cmdlets**, funções, aliases e scripts disponíveis na sessão atual do PowerShell.  
É uma ferramenta essencial para **descobrir quais comandos estão disponíveis**.

Cada resultado retornado pelo `Get-Command` é um objeto do tipo **CommandInfo**, com diversas **propriedades** que podem ser usadas para **filtrar os comandos** com base em critérios específicos.

---

### 🆘 `Get-Help`

Exibe informações detalhadas sobre um cmdlet:
- Uso
- Parâmetros
- Exemplos

Este cmdlet é **fundamental** para aprender a usar comandos no PowerShell.

💡 **Dica:** Use `-Examples` ao final para ver exemplos práticos:
```powershell
Get-Help Get-Process -Examples
