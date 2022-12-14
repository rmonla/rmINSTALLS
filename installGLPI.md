# Repositorio base [glpi-project/glpi](https://github.com/glpi-project/glpi)

- A web server (Apache, Nginx, IIS, etc.)
- MariaDB >= 10.2 or MySQL >= 5.7
- PHP (See compatibility matrix below)


## Referencia 1 [How To Install GLPI on Ubuntu 20.04/18.04](https://computingforgeeks.com/how-to-install-glpi-on-ubuntu-linux/)

### Paso 1: Actualizar índices y repoositorios.
    
    sudo apt update && sudo apt upgrade -y

### Paso 2: Instalar Base de Datos MariaDB

    sudo apt install mariadb-server mariadb-client
    sudo mysql_secure_installation $colegioAAA99

Despues de la instalación, logearse como root de labase de datos.

    sudo mysql -u root -p
    UPDATE mysql.user SET plugin = 'mysql_native_password' WHERE User = 'root';
    FLUSH PRIVILEGES;
    QUIT;
    
Crear Base de Datos y Usuario del GLPI.

    mysql -u root -p
    CREATE DATABASE glpi;
    CREATE USER 'glpi'@'localhost' IDENTIFIED BY '$isaeGLPI00';
    GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';
    FLUSH PRIVILEGES;
    EXIT;    

### Paso 3: Instalar PHP y Apache

Instalar PHP

    sudo apt-get -y install php php-{curl,gd,imagick,intl,apcu,recode,memcache,imap,mysql,cas,ldap,tidy,pear,xmlrpc,pspell,gettext,mbstring,json,iconv,xml,gd,xsl}

Instalar Apache  
    
    sudo apt-get -y install apache2 libapache2-mod-php

### Paso 4: Descargar e instalar GLPI

Ver [última versión del GLPI](https://glpi-project.org/downloads/) 
        
    export VER="10.0.2"
    wget https://github.com/glpi-project/glpi/releases/download/$VER/glpi-$VER.tgz

Descomprimo y paso al directorio del apache.   
    
    tar xvf glpi-$VER.tgz
    sudo mv glpi /var/www/html/
    
Activo permisos en el directosrio.

    sudo chown -R www-data:www-data /var/www/html/
       
### Paso 5: Último seguir los pasos del asistente de instalación del GLPI.

[http://127.0.0.1/glpi/install/install.php](http://127.0.0.1/glpi/install/install.php)

