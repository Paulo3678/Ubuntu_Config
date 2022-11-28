<p align="center">
    <img src="/images/ubuntu.png"/>
</p>

Este documento foi criado para ajudar aqueles que, como eu, precisam configurar em um máquina o Apache, PHP, Virtual Hosts e o MySQL.
<br>
Viso ajudar o máximo de pessoas possíveis, então, se não for pedir muito hehe compartilhe com algum amigo 😁.

<p align="center">
    <img src="/images/apache.png" width="200"/>
</p>

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

<br>

<hr>

<p align="center">
    <img src="/images/php.png" width="200"/>
</p>
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


<p align="center">
    <img src="/images/composer.png" width="200"/>
</p>

#Configurando Composer

> sudo su <br>
**Para entra no modo de super usuário**

> apt-get update <br>
**Verificando atualizações**

> sudo apt install curl <br>
**Instala o curl, usado para baixar o composer** <br>
> sudo apt install php-cli unzip <br>
**Instala a cli unzip do php, para extrair o arquivo do composer** <br>

> curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
**Baixa o instalador do composer**

> HASH=`curl -sS https://composer.github.io/installer.sig`
**Configura o hash do instalador**

<h6>-- Verifcando o instalação</h6>

> echo $HASH <br>
>> **Output** <br>
>>e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a 

>php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" <br>
>> **Output** <br>
>>Installer verified

> sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer <br>
>> **Output** <br>
>>All settings correct for using Composer <br>
>>Downloading... <br>
>>Composer (version 2.2.9) successfully installed to: /usr/local/bin/composer <br>
>>Use it: php /usr/local/bin/composer


> composer
> **Roda o composer**
<hr>

<p align="center">
    <img src="/images/mysql.png" width="200"/>
</p>

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


<p align="center">
    <img src="/images/vhost.png" width="200"/>
</p>

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


> &lt;VirtualHost *:80&gt; </br>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerAdmin admin@example.com <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerName example.com <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerAlias site.com.br <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;DocumentRoot /var/www/html/teste <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ErrorLog &#x24;{APACHE_LOG_DIR}/error.log <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;CustomLog &#x24;{APACHE_LOG_DIR}/access.log combined <br/>
&lt;/VirtualHost&gt;
<br>
**Configuração para qualquer arquivo .conf criado futuramente, sendo necessário trocar apenas o "meusite.com.br" e o "/projeto"**

