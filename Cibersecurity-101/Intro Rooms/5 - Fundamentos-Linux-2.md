# LINUX FUNDAMENTALS 2
## SECURE SHELL

### O que é SSH e como funciona?
SSH (Secure Shell) é simplesmente um protocolo usado para comunicação segura entre dispositivos, de forma criptografada.

Utilizando criptografia, qualquer entrada que enviamos em formato legível por humanos (como comandos ou textos) é criptografada para ser transmitida pela rede — onde então é descriptografada quando chega na máquina remota (por exemplo, um servidor Linux).

Você pode aprender sobre os diferentes tipos de criptografia em uma sala do TryHackMe. Mas por agora, só precisamos entender que:
SSH permite que executemos comandos remotamente em outro dispositivo (por exemplo, acessar um servidor e controlar ele de onde você estiver).

Qualquer dado enviado entre os dispositivos é criptografado quando passa pela rede, como a Internet (ou seja, outras pessoas não conseguem ver o conteúdo mesmo que interceptem a conexão).

O exercício consiste em utilizar uma máquina virtual Linux e o protocolo SSH para se conectar remotamente a outra máquina, empregando o endereço IP da máquina remota e as credenciais necessárias para realizar o login.
Feito isso em laboratório.

A maioria dos comandos permite que argumentos sejam fornecidos. Esses argumentos são identificados por um hífen e uma determinada palavra-chave conhecida como flags ou switches.

Mais adiante, discutiremos como podemos identificar quais comandos permitem argumentos e entender o que esses fazem exatamente.
Ao usar um comando, a menos que especificado de outra forma, ele executará seu comportamento padrão. Por exemplo, ls lista o conteúdo do diretório de trabalho. 

No entanto, arquivos ocultos não são exibidos. Podemos usar flags e switches para estender o comportamento dos comandos.

Usando nosso exemplo de ls, o comando ls nos informa que há apenas uma pasta chamada "folder1", conforme destacado na captura de tela abaixo. 
Observe que os conteúdos nas capturas de tela abaixo são apenas exemplos.

No entanto, ao usarmos o argumento -a (abreviação de --all), passamos a ter uma saída com mais arquivos e pastas, como por exemplo ".hiddenfolder". Arquivos e pastas que começam com "." são considerados arquivos ocultos.

Comandos que aceitam argumentos também costumam ter a opção --help. Essa opção lista as opções disponíveis que o comando aceita, fornece uma breve descrição e um exemplo de uso.

Essa opção é, na verdade, uma versão formatada do que chamamos de man page (abreviação de manual), que contém a documentação dos comandos e aplicativos do Linux.

### A Página de Manual (Man Page)
As páginas de manual são uma excelente fonte de informação sobre comandos do sistema e aplicativos disponíveis em uma máquina Linux, acessíveis tanto localmente quanto online.
Para acessar essa documentação, usamos o comando man seguido do comando desejado. Usando nosso exemplo com ls, utilizaríamos man ls para visualizar as páginas de manual do ls.

## SISTEMAS DE ARQUIVOS

Cobrimos alguns dos comandos mais fundamentais ao interagir com o sistema de arquivos em uma máquina Linux. Por exemplo, vimos como listar e encontrar conteúdos de pastas usando ls e find, além de navegar pelo sistema de arquivos com cd.

Nesta tarefa, vamos aprender mais comandos para interagir com o sistema de arquivos, permitindo que a gente:
- crie arquivos e pastas
- mova arquivos e pastas
- exclua arquivos e pastas

Mais especificamente, os seguintes comandos:
- touch: Cria um arquivo
- mkdir: Cria uma pasta (diretório)
- cp: Copia um arquivo ou pasta
- mv: Move um arquivo ou pasta
- rm: Remove (deleta) um arquivo ou pasta
- file: Identifica o tipo de um arquivo

💡 Dica: Assim como com o comando cat, podemos fornecer caminhos completos (ex: diretorio1/diretorio2/note) para todos esses comandos.

### Criando Arquivos e Pastas (touch, mkdir)

Criar arquivos e pastas no Linux é um processo simples.
Primeiro, vamos cobrir a criação de um arquivo. O comando touch recebe apenas um argumento — o nome que queremos dar ao arquivo. Por exemplo, podemos criar um arquivo chamado "note" usando: touch note.

📝 Importante: o touch cria apenas um arquivo em branco. Para adicionar conteúdo, é necessário usar comandos como echo ou editores de texto como nano.

Este é um processo semelhante para criar uma pasta, o que envolve apenas usar o comando mkdir e novamente fornecer o nome que queremos atribuir ao diretório.

Por exemplo, criando o diretório "mydirectory" usando mkdir mydirectory.

### Removendo Arquivos e Pastas (rm)

rm é extraordinário dentre os comandos que cobrimos até agora. Você pode simplesmente remover arquivos usando rm. No entanto, você precisa fornecer a opção -R junto com o nome do diretório que deseja remover.

### Copiando e Movendo Arquivos e Pastas (cp, mv)

Copiar e mover arquivos é uma funcionalidade importante em uma máquina Linux. Começando com cp, esse comando recebe dois argumentos:
- o nome do arquivo existente
- o nome que desejamos atribuir ao novo arquivo ao copiar

cp copia todo o conteúdo do arquivo existente para o novo arquivo. 

Mover um arquivo recebe dois argumentos, assim como o comando cp. No entanto, em vez de copiar e/ou criar um novo arquivo, mv irá mesclar ou modificar o segundo arquivo que fornecemos como argumento.

Você pode usar mv não apenas para mover um arquivo para uma nova pasta, mas também para renomear um arquivo ou pasta. Por exemplo, estamos renomeando o arquivo "note2" para "note3". "note3" agora terá o conteúdo de "note2".

Seria como se você estivesse colocando um arquivo em cima do outro, substituindo o conteúdo daquele arquivo pelo conteúdo do primeiro arquivo. 

### Determinando o tipo do arquivo

O que muitas vezes é enganoso e confunde as pessoas é presumir qual é o propósito ou conteúdo de um arquivo apenas com base no nome dele.
Arquivos geralmente têm o que é conhecido como extensão para facilitar isso. 

Por exemplo, arquivos de texto geralmente têm a extensão ".txt". Mas isso não é obrigatório.

Até agora, os arquivos que usamos nos exemplos não tinham extensão. E sem saber o contexto de por que o arquivo está lá — não sabemos realmente seu propósito.

Aí entra o comando file. Esse comando recebe um argumento: o nome do arquivo. Por exemplo, podemos usar:
- file note
Isso serve para verificar se o arquivo "note" é mesmo um arquivo de texto (ou outro tipo de arquivo).

O comando irá analisar o conteúdo real do arquivo, não apenas o nome.

## PERMISSÕES 101
Como você já deve ter percebido até agora, certos usuários não podem acessar determinados arquivos ou pastas. Já exploramos alguns comandos que podem ser usados para determinar quais acessos temos e onde eles nos levam.

Nas tarefas anteriores, aprendemos como expandir o uso dos comandos por meio de flags e opções (também chamadas de switches). 

Pegue como exemplo o comando ls, que lista o conteúdo do diretório atual. Ao usar o switch -l, podemos ver colunas.

Embora pareçam intimidantes, essas três colunas são muito importantes para determinar certas características de um arquivo ou pasta e se temos ou não acesso a eles. 

Um arquivo ou pasta pode ter algumas características que definem quais ações são permitidas e qual usuário ou grupo pode realizar essas ações, como as seguintes:
- Read (leitura)
- Write (escrita)
- Execute (execução)

### Diferenças entre Usuários e Grupos (resumidamente)

Uma grande vantagem do Linux é que suas permissões são muito granulares. Mesmo que um usuário seja o dono de um arquivo, se as permissões forem configuradas corretamente, um grupo de usuários também pode ter permissões diferentes ou iguais no mesmo arquivo, sem afetar o dono original.

Exemplo real: o usuário do sistema que executa um servidor web precisa de permissões para ler e escrever arquivos. 

Porém, empresas de hospedagem precisam permitir que clientes enviem seus próprios arquivos para o site sem que sejam o usuário do servidor web, o que evita comprometer a segurança dos outros clientes.

### Alternando Entre Usuários
Trocar de usuário no Linux é fácil graças ao comando su (substitute user). A menos que você seja o usuário root (ou use o sudo), você precisa saber duas coisas para mudar de usuário:
- O nome do usuário para o qual deseja mudar
- A senha desse usuário

O comando su aceita algumas opções úteis (chamadas switches). Por exemplo, executar um comando ao entrar ou definir um shell específico. Você pode ler mais no manual do su (man su), mas aqui vamos focar no switch -l ou --login.

Ao usar -l com su, você inicia uma sessão que simula o login completo do novo usuário — ou seja, você herda variáveis de ambiente e outras configurações desse usuário.

Usando su para trocar para o usuário user2 (modo padrão):
tryhackme@linux2:~$ su user2  
Password:  
user2@linux2:/home/tryhackme$

Aqui, a nova sessão permanece no diretório do usuário anterior. Usando su -l para trocar para o usuário user2 (modo completo de login):
tryhackme@linux2:~$ su -l user2  
Password:  
user2@linux2:~$ pwd  
/home/user2

Agora, a nova sessão entra diretamente no diretório do usuário user2.

## DIRETÓRIOS COMUNS
### /etc
Esse diretório raiz é um dos mais importantes do sistema. A pasta etc (abreviação de et cetera) é um local comum para armazenar arquivos de configuração do sistema, usados pelo sistema operacional.

Por exemplo, o arquivo sudoers contém a lista de usuários e grupos que têm permissão para executar comandos com sudo (ou seja, como root).

Também são destacados os arquivos passwd e shadow. Esses arquivos são especiais no Linux pois mostram como o sistema armazena as senhas de cada usuário, de forma criptografada usando SHA-512.

🗂️ Alguns conteúdos notáveis do diretório /etc:
shadow  passwd  sudoers  sudoers.d

### /var
O diretório /var (abreviação de variable, ou variável) é um dos diretórios principais do sistema. Ele guarda dados que são frequentemente acessados ou modificados por serviços ou aplicativos do sistema.

Por exemplo, arquivos de log (/var/log) ou dados que não pertencem diretamente a um usuário, como bancos de dados.

🗂️ Alguns conteúdos notáveis do diretório /var:
backups  log  opt  tmp

### /root
Diferente do diretório /home, o diretório /root é o diretório pessoal do usuário root (o administrador do sistema).

Não há nada de especial além de entender que é o “home” do usuário root, e não está dentro de /home como os demais usuários — o que pode confundir.

🗂️ Alguns conteúdos notáveis do diretório /root:
myfile  myfolder  passwords.xlsx

### /tmp
Esse é um diretório raiz único no Linux. Abreviação de temporary (temporário), o /tmp é volátil, ou seja: os dados armazenados aqui são temporários e são apagados ao reiniciar o sistema (como a memória RAM).

🔐 Para pentesting, o /tmp é útil pois qualquer usuário pode escrever nesse diretório por padrão. Ou seja, se ganharmos acesso à máquina, é um ótimo local para armazenar scripts e ferramentas temporárias (como de enumeração).

🗂️ Alguns conteúdos notáveis do diretório /tmp:
todelete  trash.txt  rubbish.bin
