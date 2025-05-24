
# LINUX FUNDAMENTALS 3

## EDITORES DE TEXTO DO TERMINAL

# Armazenamento de texto com echo e redirecionamento
# > sobrescreve o conteúdo do arquivo
# >> adiciona ao final

# Nano (editor simples)
nano nome-do-arquivo

# Comandos úteis no nano:
# Ctrl + X : sair
# Ctrl + W : pesquisar
# Ctrl + K : cortar
# Ctrl + U : colar
# Ctrl + _ : ir para linha

# VIM (editor avançado)
# Altamente personalizável, syntax highlighting, funciona em qualquer terminal

# Wget (baixar arquivos da web)
wget https://assets.tryhackme.com/additional/file.txt

# wget suporta HTTP e HTTPS
# Para ignorar SSL inválido:
wget --no-check-certificate https://siteinseguro.com/arquivo.txt

# SCP (copiar arquivos com SSH)
scp important.txt ubuntu@192.168.2.38:/home/ubuntu/transferred.txt

# SSH criptografa os dados por padrão
# Usa criptografia assimétrica na autenticação, depois simétrica na transferência

# Servindo arquivos localmente com Python
python3 -m http.server

# Por padrão, usa a porta 8000
# Disponível apenas para a rede local
# Para acessar: wget http://IP_LOCAL:8000/arquivo.txt

# PROCESSOS 101

# Visualizar processos do usuário atual
ps

# Visualizar todos os processos
ps aux

# Visualização em tempo real
top

# Finalizar processo pelo PID
kill PID

# Sinais:
# SIGTERM: finalização limpa
# SIGKILL: finalização imediata
# SIGSTOP: pausa o processo

# Namespaces isolam recursos dos processos
# PID 0: processo init do sistema (ex: systemd)

# systemctl (gerenciar serviços)
systemctl start apache2
systemctl stop apache2
systemctl enable apache2
systemctl disable apache2

# Foreground vs Background
# Comando foreground:
echo "Hi THM"
# Comando background:
echo "Hi THM" &
# Suspender e mover para background com Ctrl + Z

# CRONTAB (agendar tarefas)
# Sintaxe: MIN HOUR DOM MON DOW CMD

# Exemplo: backup a cada 12 horas
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/

# cp -R: cópia recursiva
# Substitui arquivos existentes com o mesmo nome
# Adiciona arquivos novos, mas não remove os que foram deletados na origem
