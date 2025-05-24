
# Linux Fundamentals 1

## Introdução

Bem-vindo à primeira parte da série de salas "Fundamentos de Linux".

Você provavelmente está usando uma máquina com Windows ou Mac, ambos diferentes em design visual e modo de operação. Assim como o Windows, iOS e MacOS, o Linux é apenas outro sistema operacional — e um dos mais populares do mundo, alimentando:

- Carros inteligentes  
- Dispositivos Android  
- Supercomputadores  
- Eletrodomésticos  
- Servidores corporativos  
- Muito mais  

Nesta sala, você vai:

- Executar seus primeiros comandos em uma máquina Linux interativa no navegador  
- Aprender comandos essenciais usados para interagir com o sistema de arquivos  
- Buscar arquivos e introduzir operadores de shell  

---

## O Background do Linux

### Onde o Linux é Usado?

O Linux pode parecer mais intimidador de aprender que o Windows, mas tem suas vantagens:

- **Leveza**: Roda em hardwares simples  
- **Onipresença**: Usado em:
  - Sites
  - Painéis de carros
  - Sistemas de ponto de venda (PoS)
  - Infraestruturas críticas (semáforos, sensores industriais)

### Versões do Linux (Flavours of Linux)

"Linux" é um termo genérico para sistemas baseados em UNIX. Por ser **open-source**, existem várias variantes com usos diferentes.

- **Exemplos populares**:
  - **Ubuntu** e **Debian** (extensíveis, para desktop ou servidor)
  - **Ubuntu Server** roda com apenas 512MB de RAM!

Assim como o Windows possui versões (7, 8, 10), o Linux possui distribuições diferentes.

---

## Alguns Comandos do Linux

### ✅ 1. `echo`

- Exibe uma mensagem no terminal  
```bash
echo Hello, world!
```

### ✅ 2. `whoami`

- Mostra o nome do usuário atual  
```bash
whoami
```

### ✅ 3. `pwd` (print working directory)

- Mostra o diretório atual  
```bash
pwd
```

### ✅ 4. `ls`

- Lista arquivos e diretórios  
```bash
ls
ls -l   # mostra detalhes como permissões, tamanho e data
```

### ✅ 5. `cd` (change directory)

- Muda de diretório  
```bash
cd Downloads
cd ..   # volta um nível
```

### ✅ 6. `clear`

- Limpa o terminal  
```bash
clear
```

### ✅ 7. `touch`

- Cria um arquivo vazio  
```bash
touch novo.txt
```

### ✅ 8. `mkdir`

- Cria uma nova pasta  
```bash
mkdir projetos
```

### ✅ 9. `rm`

- Remove arquivos e diretórios  
```bash
rm arquivo.txt
rm -r pasta/  # remove pasta inteira
```
⚠️ Use com cuidado!

### ✅ 10. `cat`

- Mostra o conteúdo de um arquivo  
```bash
cat notas.txt
```

---

## Comando `find`

Permite buscar arquivos rapidamente sem depender de `cd` e `ls`.

### Exemplo 1: Procurar por nome
```bash
find -name passwords.txt
```

### Exemplo 2: Procurar por extensão
```bash
find -name "*.txt"
```
> Resultado:
```
/folder/note.txt
```

---

## Usando `grep`

Busca dentro dos arquivos por termos específicos.

### Exemplo: Procurar IP no log
```bash
grep "81.143.211.90" access.log
```
> Saída:
```
81.143.211.90 - - [25/Mar/2021:11:17 +0000] "GET / HTTP/1.1" 200 417 "-" ...
```

---

## Operadores do Linux

Aprenda operadores importantes para aprimorar seu uso do terminal.

| Operador | Função |
|----------|--------|
| `&`      | Executa comandos em segundo plano |
| `&&`     | Encadeia comandos (executa o segundo se o primeiro for bem-sucedido) |
| `>`      | Redireciona a saída para um arquivo (sobrescreve) |
| `>>`     | Redireciona a saída para um arquivo (acrescenta) |

### Operador `&`
Executa comandos em segundo plano:
```bash
cp arquivo_grande.zip destino/ &
```

### Operador `&&`
Executa comandos em sequência:
```bash
mkdir nova_pasta && cd nova_pasta
```

### Operador `>`
Redireciona a saída:
```bash
echo hey > welcome
cat welcome  # saída: hey
```

### Operador `>>`
Acrescenta ao final do arquivo:
```bash
echo hello >> welcome
cat welcome
# saída:
# hey
# hello
```
