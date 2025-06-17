# LINUX FUNDAMENTALS 3
## EDITORES DE TEXTO DO TERMINAL
Ao longo desta série até agora, armazenamos texto em arquivos usando uma combinação do comando echo e os operadores de redirecionamento > e >>.

No entanto, essa não é uma forma eficiente de lidar com dados, especialmente quando se trabalha com arquivos com várias linhas e afins.
Apresentando os editores de texto no terminal

Existem algumas opções que você pode usar, cada uma com níveis diferentes de facilidade e funcionalidades. Essa tarefa vai te apresentar ao nano, mas também mostrar uma alternativa chamada VIM.

### INFORMATIVO:
1 - O operador > sobrescreve o conteúdo do arquivo, enquanto >> adiciona texto ao final sem apagar o que já existe.
2 - Por padrão, o Nano cria arquivos de texto simples (sem formatação ou extensão específica).

### Nano
É fácil começar a usar o Nano! Para criar ou editar um arquivo com o nano, basta usar o comando:
nano nome-do-arquivo
(substitua "nome-do-arquivo" pelo nome do arquivo que você deseja editar). 
Depois que você pressiona Enter, o Nano será iniciado, e você pode começar a digitar ou modificar o texto.

Use as setas para cima e para baixo para navegar entre as linhas. Use Enter para começar uma nova linha.

O Nano possui recursos simples e úteis, cobrindo o básico que você esperaria de um editor de texto:
- Pesquisar texto
- Copiar e colar
- Ir para um número específico de linha
- Ver em qual linha você está

Para usar essas funções, pressione a tecla Ctrl (representada como ^ no Linux) e a letra correspondente. Por exemplo, para sair, pressione Ctrl + X.

### VIM
O VIM é um editor de texto muito mais avançado. Embora você não precise saber todos os recursos avançados, é útil mencioná-lo para aprimorar suas habilidades no Linux.

Alguns dos benefícios do VIM, mesmo que leve mais tempo para se acostumar, incluem:
- Altamente personalizável – você pode modificar os atalhos do teclado conforme sua preferência.
- Realce de sintaxe (Syntax Highlighting) – muito útil ao escrever ou manter códigos, o que o torna popular entre desenvolvedores de software.
- Funciona em todos os terminais, enquanto o nano pode não estar instalado em alguns.
- Existem muitos recursos de apoio, como cheatsheets (folhas de referência rápida), tutoriais e outros.

## UTILIDADES GERAIS

### Baixando Arquivos (Wget)
Uma função fundamental da computação é a capacidade de transferir arquivos. Por exemplo, você pode querer baixar um programa, um script ou até uma imagem. Felizmente, existem várias maneiras de recuperar esses arquivos.

Vamos abordar o uso do comando wget. Esse comando nos permite baixar arquivos da web via HTTP — como se você estivesse acessando o arquivo diretamente no navegador.

Basta fornecer o endereço (URL) do recurso que deseja baixar. Por exemplo, se eu quisesse baixar um arquivo chamado "myfile.txt" para a minha máquina, sabendo o endereço da web, seria algo assim:
- wget   https://assets.tryhackme.com/additional/file.txt

Esse comando irá fazer o download do arquivo dentro do diretório que você estiver no momento.

### INFORMATIVO
O wget funciona tanto em sites com http e https?
- O wget suporta HTTPS nativamente e consegue baixar arquivos de sites seguros (com HTTPS), desde que:

O site permita acesso direto ao arquivo (sem autenticação ou bloqueios específicos);
- O certificado SSL do site seja válido (ou você esteja disposto a ignorar avisos com a flag --no-check-certificate).

## Transferindo Arquivos do Seu Host - SCP (SSH)

SCP (Secure Copy) é exatamente isso — uma forma segura de copiar arquivos. 
Diferente do comando cp tradicional, o scp permite transferir arquivos entre dois computadores usando o protocolo SSH, garantindo autenticação e criptografia.

Seguindo o modelo de ORIGEM e DESTINO, o scp permite:
- Copiar arquivos e diretórios do seu sistema local para um sistema remoto
- Copiar arquivos e diretórios de um sistema remoto para o seu sistema local, desde que você saiba os nomes de usuário e senhas de ambos os sistemas (local e remoto).

Seria mais ou menos da seguinte maneira:
scp important.txt(essa seria a fonte) ubuntu@192.168.2.38: /home/ubuntu/transferred.txt (para onde o arquivo vai).

### INFORMATIVO
O SSH criptografa todos os dados transferidos por padrão, garantindo sigilo e segurança na comunicação.

O SSH usa criptografia assimétrica para a autenticação inicial e troca de chaves, e depois criptografia simétrica para transferir os dados de forma eficiente.

## Servindo Arquivos a Partir do Seu Host – WEB

Máquinas Ubuntu já vêm com o Python3 instalado. O Python oferece um módulo leve e fácil de usar chamado HTTPServer, que transforma seu computador em um servidor web simples e rápido, permitindo que você disponibilize arquivos para outros computadores baixarem, usando comandos como curl ou wget.

### Como funciona?
O HTTPServer do Python3 serve os arquivos do diretório em que o comando for executado. Isso pode ser alterado com opções específicas (consulte o manual do comando para detalhes).
python3 -m http.server

Basta rodar esse comando no terminal, e seu computador começa a servir os arquivos do diretório atual via HTTP.

Exemplo prático:
Você está no diretório chamado "webserver", que contém um único arquivo chamado "file". Ao rodar o comando acima nesse diretório, qualquer outro computador na rede poderá acessar e baixar esse arquivo através do navegador ou ferramentas como wget.

### INFORMATIVO
O Python usa o protocolo HTTP para transformar sua máquina temporariamente em um servidor web. O servidor funciona apenas enquanto o comando estiver rodando — ao encerrar o terminal ou pressionar Ctrl+C, ele para.

O http.server do Python, por padrão, abre sua máquina apenas para a rede local (LAN), ou seja, outros dispositivos conectados na mesma rede que você.

Se você quiser que a máquina fique acessível pela web (internet), seria necessário configurar o roteador para redirecionar a porta 8000 (port forwarding), o que não é recomendado sem medidas de segurança, pois abriria sua máquina para acesso público.

## EXEMPLO PRÁTICO FEITO
Abri o terminal no usuário root@ip-10-10-223-176 e digitei o comando ssh tryhackme@10.10.18.228. Inseri a senha “tryhackme” e acessei remotamente a máquina do usuário tryhackme@linux3.

Nesta máquina, digitei o comando ls para verificar quais arquivos se encontravam neste diretório e descobri que havia apenas o arquivo task3. Depois, digitei o comando python3 -m http.server onde, por padrão, abri a porta 8000 para a rede local. 

Abri outro terminal no linux, onde ele abriu novamente no usuário root@ip-10-10-223-176 e digitei o comando:
wget http://10.10.18.228:8000/task3

A partir daqui, o usuário root fez o download remoto do arquivo task3 do usuário tryhackme que tinha a porta 8000 aberta para a rede local.

## PROCESSOS 101
Processos são os programas que estão sendo executados na sua máquina. Eles são gerenciados pelo kernel, e cada processo possui um ID associado a ele, conhecido como PID. 

O PID é incrementado conforme a ordem em que os processos são iniciados. Ou seja, o 60º processo terá o PID 60.

### Visualizando Processos
Podemos usar o comando amigável ps para exibir uma lista dos processos em execução na sessão do nosso usuário, junto com informações adicionais, como:
- Código de status
- Sessão que está executando o processo
- Tempo de uso da CPU
- Nome do programa ou comando que está sendo executado

Explicação da imagem:
PID (Process ID):
102: É o processo do bash, o terminal atual onde você está trabalhando.
204: É o processo do próprio comando ps, criado no momento da execução.

TTY (Terminal):
pts/1: Refere-se ao terminal virtual (pseudo-terminal) onde esses processos estão rodando.

TIME (CPU Time):
Ambos estão com 00:00:00, pois quase nenhum tempo de CPU foi utilizado.

CMD (Comando):
bash: É o shell interativo que está aberto.
ps: É o comando que você acabou de rodar para listar os processos.
Note como na captura de tela acima, o segundo processo ps tem um PID de 204, e então no comando abaixo dele, isso é incrementado para 205.
Para ver os processos executados por outros usuários e aqueles que não são iniciados por uma sessão (ou seja, processos do sistema), precisamos usar aux com o comando ps, assim:

Observe que podemos ver um total de 5 processos – note como agora temos os usuários "root" e "cmnatic".
Um comando muito útil também é o comando top; top fornece estatísticas em tempo real sobre os processos em execução no seu sistema, em vez de uma visualização única. 

Essas estatísticas serão atualizadas a cada 10 segundos, mas também serão atualizadas quando você usar as setas do teclado para navegar pelas várias linhas. 

Outro ótimo comando para obter informações sobre o sistema é o comando top.
Gerenciando Processos
Você pode enviar sinais que terminam processos; há uma variedade de tipos de sinais que determinam o quão "limpamente" o processo será finalizado pelo kernel. 

Para matar um comando, podemos usar o comando kill e o PID correspondente que desejamos encerrar. Por exemplo, para matar o PID 1337, usaríamos:
kill 1337

Abaixo estão alguns dos sinais que podemos enviar a um processo quando ele é encerrado:
- SIGTERM – Encerra o processo, mas permite que ele faça tarefas de limpeza antes
- SIGKILL – Encerra o processo imediatamente – sem nenhuma limpeza
- SIGSTOP – Para/suspende um processo

### Como os Processos Começam?
Vamos começar falando sobre namespaces. O Sistema Operacional (SO) usa namespaces para dividir os recursos disponíveis no computador (como CPU, RAM e prioridade) entre os processos. 

Pense nisso como dividir seu computador em fatias — semelhante a um bolo. Os processos dentro dessa fatia terão acesso a uma quantidade específica de poder de processamento, porém será apenas uma pequena parte do que está disponível para todos os processos no geral.

Os namespaces são ótimos para a segurança, pois isolam os processos uns dos outros — apenas aqueles que estão no mesmo namespace poderão se ver.
Falamos anteriormente sobre como os PIDs funcionam, e é aqui que isso entra em ação. O processo com ID 0 é um processo que é iniciado quando o sistema dá boot. 

Esse processo é o init do sistema no Ubuntu, como o systemd, que é usado para gerenciar os processos do usuário e atua entre o sistema operacional e o usuário.

Por exemplo, assim que um sistema é iniciado e inicializado, o systemd é um dos primeiros processos a rodar. Qualquer programa ou software que desejamos iniciar será iniciado como um "processo filho" do systemd. 

Isso significa que ele é controlado pelo systemd, mas executado como seu próprio processo (embora compartilhando os recursos com o systemd), tornando mais fácil a identificação e o gerenciamento.

### Fazer Processos/Serviços Iniciarem com o Sistema (Boot)

Alguns aplicativos podem ser iniciados automaticamente durante o boot do sistema que possuímos. 

Por exemplo, servidores web, servidores de banco de dados ou servidores de transferência de arquivos. Esse tipo de software costuma ser crítico e, por isso, os administradores geralmente configuram para que eles iniciem automaticamente quando o sistema liga.

Neste exemplo, vamos instruir o servidor web Apache a iniciar manualmente, e depois configurar o sistema para que ele inicie automaticamente no boot.
Entra em cena o uso do systemctl — este comando permite que a gente interaja com o processo/daemon systemd. Continuando com o nosso exemplo, systemctl é um comando fácil de usar, com o seguinte formato:

systemctl [opção] [serviço]
Por exemplo, para mandar o Apache iniciar, usamos:
systemctl start apache2
Simples, certo? Da mesma forma, se quisermos parar o Apache, basta trocar a opção por stop:
systemctl stop apache2
Podemos usar quatro opções principais com o systemctl:
Start (Iniciar)
Stop (Parar)
Enable (Ativar no boot)
Disable (Desativar no boot)

### Uma Introdução ao Conceito de Background (Plano de Fundo) e Foreground (Primeiro Plano) no Linux
Os processos podem rodar em dois estados: no plano de fundo (background) e no primeiro plano (foreground).

Por exemplo, comandos que você executa no terminal, como echo, rodam em primeiro plano, pois são os únicos comandos fornecidos e não foram instruídos a rodar em segundo plano.
O echo é um ótimo exemplo, pois o resultado (saída) do comando aparece imediatamente no terminal (foreground).

Mas se ele estivesse rodando em background, esse retorno não apareceria diretamente para você — veja o exemplo na captura de tela abaixo:

Aqui, estamos executando o comando echo "Hi THM", onde esperamos que a saída seja retornada diretamente para nós, como acontece no início.

Mas ao adicionar o operador & ao final do comando, em vez da saída, recebemos apenas o ID do processo do echo, pois ele está rodando em segundo plano (background).

Isso é ótimo para comandos como copiar arquivos, pois permite que o comando rode em segundo plano e você continue usando o terminal para outros comandos, sem precisar esperar o término da cópia.
Podemos fazer a mesma coisa com scripts — em vez de usar o operador &, podemos pressionar Ctrl + Z no teclado para colocar um processo em segundo plano.

Isso também funciona como uma forma de "pausar" a execução de um script ou comando, como mostrado no exemplo abaixo.

## MANTENDO SEU SISTEMA: AUTOMAÇÃO

Usuários podem querer agendar uma determinada ação ou tarefa para acontecer após o sistema ser iniciado. 

Por exemplo, executar comandos, fazer backup de arquivos ou iniciar seus programas favoritos, como Spotify ou Google Chrome.
Vamos falar sobre o processo cron, mas mais especificamente, sobre como podemos interagir com ele usando o crontab. O crontab é um dos processos iniciados durante a inicialização do sistema, sendo responsável por facilitar e gerenciar as tarefas agendadas (cron jobs).

Uma crontab é simplesmente um arquivo especial com uma formatação reconhecida pelo processo cron para executar cada linha passo a passo. As crontabs exigem 6 valores específicos:
- MIN: Em qual minuto executar
- HOUR: Em qual hora executar
- DOM: Em qual dia do mês executar
- MON: Em qual mês do ano executar
- DOW: Em qual dia da semana executar
- CMD: O comando que será executado

Vamos usar o exemplo de fazer backup de arquivos. Você pode querer fazer backup da pasta Documents do usuário cmnatic a cada 12 horas. O comando seria formatado assim:

0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
-R significa "recursivamente", ou seja, copia todo o conteúdo da pasta Documents, incluindo subpastas e arquivos.
O conteúdo de Documents será copiado dentro de /var/backups/, criando a pasta /var/backups/Documents.
O que acontece se já existir /var/backups/Documents?
Se a pasta /var/backups/Documents já existir, o cp apenas vai copiar por cima os arquivos com o mesmo nome, substituindo-os.

Arquivos novos serão adicionados, mas arquivos que não existem mais na origem não são apagados do destino.

Um recurso interessante das crontabs é que elas também suportam o curinga ou asterisco (*). 

Se você não quiser especificar um valor para determinado campo (por exemplo, mês ou dia), basta usar o asterisco para indicar "qualquer valor".

Isso pode ser um pouco confuso no início, por isso existem recursos úteis como o site "Crontab Generator", que ajuda a montar a linha do cron de forma mais intuitiva, e o "Cron Guru", que explica o agendamento.

Você pode editar sua crontab com o comando:
crontab -e
Ele permitirá escolher um editor de texto (como o Nano) para modificar sua crontab.

### Apresentando Pacotes e Repositórios de Software
Quando os desenvolvedores desejam submeter um software para a comunidade, eles o enviam para um repositório "apt". 
Se aprovado, seus programas e ferramentas serão liberados para o público. Dois dos aspectos mais valiosos do Linux se destacam aqui: a acessibilidade para o usuário e o mérito das ferramentas de código aberto.

Ao usar o comando ls em uma máquina Linux com Ubuntu 20.04, esses arquivos servem como o portal ou registro.
Embora os fornecedores de sistemas operacionais mantenham seus próprios repositórios, você também pode adicionar repositórios da comunidade à sua lista! 

Isso permite que você expanda as capacidades do seu sistema operacional. Repositórios adicionais podem ser adicionados usando o comando add-apt-repository ou listando outro provedor! 

Por exemplo, alguns fornecedores terão um repositório mais próximo da sua localização geográfica.

### Gerenciando Seus Repositórios (Adicionando e Removendo)
Normalmente usamos o comando apt para instalar software em nosso sistema Ubuntu. O comando apt faz parte do software de gerenciamento de pacotes que também se chama apt. 

O apt contém uma suíte completa de ferramentas que nos permite gerenciar os pacotes e fontes do nosso software, além de instalar ou remover softwares ao mesmo tempo.

Um dos métodos para adicionar repositórios é usar o comando add-apt-repository, como mostramos acima, mas vamos explorar como adicionar e remover um repositório manualmente. 

Embora você possa instalar softwares usando instaladores de pacotes como o dpkg, os benefícios do apt significam que sempre que atualizamos nosso sistema — o repositório que contém os softwares que adicionamos também é verificado em busca de atualizações.

Neste exemplo, vamos adicionar o editor de texto Sublime Text à nossa máquina Ubuntu como um repositório, já que ele não faz parte dos repositórios padrão do Ubuntu. 

Ao adicionar software, a integridade do que baixamos é garantida pelo uso do que chamamos de chaves GPG (Gnu Privacy Guard). 
Essas chaves funcionam essencialmente como uma verificação de segurança dos desenvolvedores dizendo: "aqui está o nosso software". Se as chaves não corresponderem ao que o seu sistema confia e ao que os desenvolvedores usaram, então o software não será baixado.

Portanto, para começar, precisamos adicionar a chave GPG dos desenvolvedores do Sublime Text 3. (Observe que as instâncias do TryHackMe não têm acesso à internet, então não esperamos que você adicione isso à máquina que você implantou, pois isso falharia.)

### Mantendo Seu Sistema: Logs
Nós mencionamos brevemente os arquivos de log e onde eles podem ser encontrados na parte 1 de Linux Fundamentals. 

No entanto, vamos recapitular rapidamente. Localizados no diretório /var/log, esses arquivos e pastas contêm informações de registro (logs) de aplicações e serviços que estão rodando no seu sistema. 

O sistema operacional (OS) se tornou bastante eficiente em gerenciar automaticamente esses logs em um processo conhecido como "rotação" (ou log rotation).

Aqui estão alguns exemplos de logs destacados de três serviços rodando em uma máquina Ubuntu:
Um servidor web Apache2

Logs do serviço fail2ban, que é usado para monitorar tentativas de força bruta, por exemplo
O serviço UFW, que é usado como firewall.