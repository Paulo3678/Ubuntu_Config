# Configurando Apache

> sudo su
**Para entra no modo de super usuário**

> apt-get update
**Verificando atualizações**

> apt-get install apache2
**Instala o apache**

> sudo ufw app info "Apache Full"
**Ver portas disponíveis do apache**

> sudo ufw allow in "Apache Full"
**Permitindo HTTP e HTTPS**

> apt install net-tools
**Para ver configurações da sua rede (como o ip)**

> ifconfig -a
**Para ver seu ip**

> apt install libapache2-mod-php7.3
**Configurações do php para o apache**

<!-- > chmod 777 /var/www/&lt;seu diretorio&gt; -->
<hr>

# Configurando PHP
> sudo su
**Para entra no modo de super usuário**

> apt-get update
**Verificando atualizações**

> apt -y install software-properties-common
> add-apt-repository ppa:ondrej/php
**Configurações gerais**

> apt-get update
**Atualizar repositórios**

> apt -y install php7.3
**Instala o php 7.3 (pode qualquer outra versão)**

> apt install php7.3-mysql
**Instala as configurações do mysql para o php**

<hr>

#Configurando Composer
> sudo su
**Para entra no modo de super usuário**

> apt-get update
**Verificando atualizações**

<hr>

# Configurando MySQL
> sudo su
**Para entra no modo de super usuário**

> apt-get update
**Verificando atualizações**

> apt install mysql-server
**Instala o mysql**

> mysql_secure_installation
**Inicia as configurações do MySQL**

> mysql -h localhost -u root -p
**Para loggar no MySQL**


# Configurando Virtual Host

> sudo su
**Para entra no modo de super usuário**

> nano /etc/hosts
**Abri o arquivo onde colocaremos o nome do nosso virtualhost** 
>> 127.0.0.1 meusite.com.br
**Adiciona o host ao seu computador (ctrl+o para salvar)**

> cd /etc/apache2/sites-available
**Diretório de arquivos do apache**

> cp 000-default.conf meusite.conf
**Cria um arquivo de configurações para o seu site**

> nano meusite.conf
**Para abrir o arquivo de configurações no editor do linux**

> &lt;VirtualHost *80&gt;
&nbsp;&nbsp;&nbsp;&nbsp;ServerName meusite.com.br
&nbsp;&nbsp;&nbsp;&nbsp;ServerAdmin webmaster@localhost
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Directory /var/www/projeto&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Options Indexes FollowSymLinks
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;AllowOverride All
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Require all granted
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Directory&gt;
&nbsp;&nbsp;&nbsp;&nbsp;ErrorLog &#x24;{APACHE_LOG_DIR }/error.log
&nbsp;&nbsp;&nbsp;&nbsp;CustomLog &#x24;{APACHE_LOG_DIR}/access.log combined
&lt;/VirtualHost&gt;
**Configuração para qualquer arquivo .conf criado futuramente, sendo necessário trocar apenas o "meusite.com.br" e o "/projeto"**

