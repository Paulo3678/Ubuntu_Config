# Configurando Apache

> sudo su <br>
**Para entra no modo de super usuário**

> apt-get update <br>
**Verificando atualizações**

> apt-get install apache2 <br>
**Instala o apache**

> sudo ufw app info "Apache Full" <br>
**Ver portas disponíveis do apache**

> sudo ufw allow in "Apache Full" <br>
**Permitindo HTTP e HTTPS**

> apt install net-tools <br>
**Para ver configurações da sua rede (como o ip)**

> ifconfig -a <br>
**Para ver seu ip**

> apt install libapache2-mod-php7.3 <br>
**Configurações do php para o apache**

<!-- > chmod 777 /var/www/&lt;seu diretorio&gt; --> <br>
<hr>

# Configurando PHP
> sudo su <br>
**Para entra no modo de super usuário**

> apt-get update <br>
**Verificando atualizações**

> apt -y install software-properties-common <br>
> add-apt-repository ppa:ondrej/php <br>
**Configurações gerais**

> apt-get update <br>
**Atualizar repositórios**

> apt -y install php7.3 <br>
**Instala o php 7.3 (pode qualquer outra versão)**

> apt install php7.3-mysql <br>
**Instala as configurações do mysql para o php**

<hr>

#Configurando Composer
> sudo su <br>
**Para entra no modo de super usuário**

> apt-get update <br>
**Verificando atualizações**

<hr>

# Configurando MySQL
> sudo su <br>
**Para entra no modo de super usuário**

> apt-get update <br>
**Verificando atualizações**

> apt install mysql-server <br>
**Instala o mysql**

> mysql_secure_installation <br>
**Inicia as configurações do MySQL**

> mysql -h localhost -u root -p <br>
**Para loggar no MySQL**


# Configurando Virtual Host

> sudo su <br> <br>
**Para entra no modo de super usuário**

> nano /etc/hosts <br>
**Abri o arquivo onde colocaremos o nome do nosso virtualhost** 
>> 127.0.0.1 meusite.com.br <br>
**Adiciona o host ao seu computador (ctrl+o para salvar)**

> cd /etc/apache2/sites-available <br>
**Diretório de arquivos do apache**

> cp 000-default.conf meusite.conf <br>
**Cria um arquivo de configurações para o seu site**

> nano meusite.conf <br>
**Para abrir o arquivo de configurações no editor do linux**

> &lt;VirtualHost *80&gt; <br>
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
<br>
**Configuração para qualquer arquivo .conf criado futuramente, sendo necessário trocar apenas o "meusite.com.br" e o "/projeto"**

