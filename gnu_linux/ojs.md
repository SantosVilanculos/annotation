# OJS

## Configuração

### Pré-requisitos

- Servidor Ubuntu 20.04 ou mais recente.
- Conhecimento básico do editor de texto Nano.
- O utilitário wget instalado.

### Instalar Apache

1. Instalar o servidor web Apache.

   ```sh
   sudo apt install apache2 -y
   ```

### Configurar PHP

1. Adicionar repositório PHP:

   ```sh
   sudo add-apt-repository ppa:ondrej/php
   ```

2. Instalar PHP:

   ```sh
   sudo apt-get install -y libapache2-mod-php php8.2 php8.2-cli php8.2-common php8.2-fpm php8.2-mysql php-sqlite3 php8.2-pgsql php8.2-zip php8.2-gd php8.2-mbstring php8.2-curl php8.2-xml php8.2-bcmath php8.2-tokenizer php8.2-gd php8.2-intl php8.2-zip php8.2-tidy php8.2-imagick
   ```

### Configurar Banco de Dados

1. Instalar o MariaDB:

   ```sh
   sudo apt install mariadb-server -y
   ```

2. Fazer login no MariaDB:

   ```sh
   sudo mariadb
   ```

3. Criar uma conta `ojs` e um banco de dados `ojs` para o OJS com a senha `password`:

   ```sql
   CREATE DATABASE ojs;
   GRANT ALL PRIVILEGES ON ojs.* TO 'ojs'@'localhost' IDENTIFIED BY 'password';
   FLUSH PRIVILEGES;
   exit
   ```

### Baixar o OJS, Configurar Pastas e Permitir Acesso às Suas Pastas

1. Baixar o OJS (56MB):

   ```sh
   cd ~/
   wget https://pkp.sfu.ca/ojs/download/ojs-3.4.0-5.tar.gz
   ```

2. Descompactar o arquivo baixado:

   ```sh
   tar xzvf ojs-3.4.0-5.tar.gz
   ```

3. Mover o aplicativo OJS para o diretório de aplicação criado anteriormente:

   ```sh
   sudo mv ojs-3.4.0-5/ /var/www/ojs/application
   ```

4. Criar os diretórios `ojs` e `storage` dentro da pasta `www`:

   ```sh
   sudo mkdir -p /var/www/ojs/
   sudo mkdir -p /var/www/ojs/storage
   ```

5. Modificar o proprietário para `www-data`:

   ```sh
   sudo chown -R www-data:www-data /var/www/ojs/application
   sudo chown -R www-data:www-data /var/www/ojs/storage
   ```

6. Habilitar acesso de leitura para todos os serviços da web:

   ```sh
   sudo chmod -R 755 /var/www/ojs/application
   sudo chmod -R 755 /var/www/ojs/storage
   ```

### Configurando Virtual Host

1. Criar um host virtual:

   ```sh
   sudo nano /etc/apache2/sites-available/ojs.conf
   ```

   Coloque este conteúdo no `ojs.conf`:

   ```xml
   <VirtualHost *:80>
       DocumentRoot /var/www/ojs/application/

       <Directory /var/www/ojs/application/>
               Options -Indexes +FollowSymLinks +MultiViews
               AllowOverride All
               Require all granted
       </Directory>

       ErrorLog ${APACHE_LOG_DIR}/ojs.id_error.log
       CustomLog ${APACHE_LOG_DIR}/ojs.id_requests.log combined
   </VirtualHost>
   ```

2. Desativar o host virtual padrão do Apache:

   ```sh
   sudo a2dissite 000-default.conf
   sudo systemctl restart apache2
   ```

3. Habilitar o host virtual personalizado:

   ```sh
   sudo a2ensite ojs.conf
   sudo a2enmod rewrite
   sudo systemctl restart apache2
   ```

### Carregando Arquivos PHP Primeiro no Servidor

Editar `/etc/apache2/mods-enabled/dir.conf` para que o primeiro arquivo a ser carregado seja `index.php`.

Abra com o Nano:

```sh
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Mova `index.php` para o início, como no exemplo abaixo do arquivo:

```xml
DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
```

### Configurando Acesso Externo

1. Habilitar portas do Apache para acesso externo:

   - Para HTTP, porta 80 do Apache:

     ```sh
     sudo ufw allow 80
     ```

   - Para HTTPS, porta 443 do Apache:

     ```sh
     sudo ufw allow 443
     ```

2. Habilitar acesso SSH:

   - Porta SSH 22:

     ```sh
     sudo ufw allow 22
     ```
