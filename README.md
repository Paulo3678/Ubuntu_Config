<p align="center">
    <img src="./images/ubuntu.png"/>
</p>

Este documento foi criado para ajudar aqueles que, como eu, precisam configurar em um máquina o Apache, PHP, Virtual Hosts e o MySQL.
<br>
Viso ajudar o máximo de pessoas possíveis, então, se não for pedir muito hehe compartilhe com algum amigo 😁.



<p align="center">
    <img src="./images/php.png" width="200"/>
</p>

# Configurando PHP


1º Atualizar pacotes do sistema <br>
> sudo apt-get update <br>

2º Configurações gerais do PHP  <br>
> sudo apt -y install software-properties-common <br>
> sudo add-apt-repository ppa:ondrej/php <br>

3º Atualizar pacotes do sistema <br>
> sudo apt-get update <br>

4º Instalando o php (Pode ser qualquer outra versão) <br>
> sudo apt -y install php7.3 <br>

5º Instalando as configurações mysql para o php <br>
> sudo apt install php7.3-mysql <br>

6º Instalando dependências do PHP
> sudo apt-get install php7.3-mbstring <br>
> sudo apt install php7.3-xml <br>



<hr>


<p align="center">
    <img src="./images/composer.png" width="200"/>
</p>

# Configurando Composer

1º Verificar versão atual do php
> php -v

2º Atualizar pacotes do sistema <br>
> apt-get update <br>

3º Verificar versão atual do php
> php -v

<hr>

**⚠️ WARNING: Caso a versão não seja igual a que você instalou anteriormente ⬇** <br>

4º Para alterar versão do php (O "update" pode alterar para a versão 8.* em versões mais atuais do ubuntu)
> sudo update-alternatives --config php

<hr>

5º Instalando o curl, usado para baixar o composer <br>
> sudo apt install curl <br>

6º Instalando a cli unzip do php, para extrair o arquivo do composer <br>
> sudo apt install php-cli unzip <br>

7º Baixando o instalador do composer <br>
> curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php <br>

8º Configurando o hash do instalador <br>
> HASH=`curl -sS https://composer.github.io/installer.sig` <br>

9º Verificando a instalação <br>
> echo $HASH <br>
>> **Output** <br>
>>e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a  <br>

>php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" <br>
>> **Output** <br>
>>Installer verified <br>

> sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer <br>
>> **Output** <br>
>>All settings correct for using Composer <br>
>>Downloading... <br>
>>Composer (version 2.2.9) successfully installed to: /usr/local/bin/composer <br>
>>Use it: php /usr/local/bin/composer <br>

10º Rodando o composer <br>
> composer <br>

<hr>

<p align="center">
    <img src="./images/apache.png" width="200"/>
</p>

# Configurando Apache

1º Entrando em super usuário <br>
> sudo su  <br>

2º Atualizar pacotes do sistema <br>
> apt-get update <br>

3º Instalando o apache <br>
> apt-get install apache2 <br>

4º Verificando portas disponiveis no apache <br>
> sudo ufw app info "Apache Full" <br>

5º Permitindo HTTP e HTTPS <br>
> sudo ufw allow in "Apache Full" <br>

6º Para ver configurações da sua rede (como o ip) <br>
> sudo apt install net-tools <br>

7º Ver seu ip <br>
> ifconfig -a <br>

8º Instalando as configurações do PHP para o apache <br>
> sudo apt install libapache2-mod-php7.3 <br>

9º Habilitando rotas do site
> Vá em /etc/apache2
> sudo nano apache2.conf
> Busque por:
>>  
    <Directory /var/www/>  
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted 
    </Directory>

>> Substitua por:
>> 
    <Directory /var/www/>  
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted 
    </Directory>


<br>

<hr>



<p align="center">
    <img src="./images/mysql.png" width="200"/>
</p>

# Configurando MySQL
1º Atualizando pacotes do sistema <br>
> sudo apt update <br>

2º Instalando o MySQL <br>
> sudo apt install mysql-server <br>

3º Abrindo o MySQL para configurar a senha <br>
> sudo mysql <br>

4º Com o MySQL iniciando no terminal digite: <br>
> alter user 'root'@'localhost' identified with mysql_native_password by 'suasenha' <br>

5º Terminando configuração <br>
> mysql_secure_installation <br>

6º Sequência de respostas sugerida <br>
> y, 0, n, y, y, y, y <br>

<hr>

<p align="center">
    <img src="./images/vhost.png" width="200"/>
</p>

# Configurando Virtual Host

1º Entrando em super usuário <br>
> sudo su <br>

2º Atualizar pacotes do sistema <br>
> apt-get update <br>

3º Acessando o arquivo onde colocaremos o nome do nosso virtualhost <br>
> nano /etc/hosts <br>
 
4º Adicionando um host ao seu computador (ctrl+o para salvar) <br>
>> 127.0.0.1 meusite.com.br <br>

5º Acessando diretório de arquivos do apache <br>
> cd /etc/apache2/sites-available <br>

6º Criando um arquivo de configurações para o seu site   <br>
> cp 000-default.conf meusite.conf <br>

7º Abrindo o arquivo de configurações no editor do linux  <br>
> nano meusite.conf <br>

8º Configuração para qualquer arquivo .conf criado futuramente, sendo necessário trocar apenas o "meusite.com.br" e o "/projeto" <br>
> &lt;VirtualHost *:80&gt; </br>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerAdmin admin@example.com <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerName example.com <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ServerAlias site.com.br <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;DocumentRoot /var/www/html/teste <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;ErrorLog &#x24;{APACHE_LOG_DIR}/error.log <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;CustomLog &#x24;{APACHE_LOG_DIR}/access.log combined <br/>
&lt;/VirtualHost&gt; <br>


9º Ativando o vhost <br>
> a2ensite meusite.conf

10º Desativando o vhost padrão <br>
> a2dissite 000-default.conf

11º Atualizando o apache com as novas configurações <br>
> systemctl reload apache2

12º Basta acessar o meusite.com.br no seu navegador preferido <br>
