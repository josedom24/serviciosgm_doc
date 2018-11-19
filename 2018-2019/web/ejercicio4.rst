Ejercicio: Instalación de un sistema LAMP
=========================================


El acrónimo ‘LAMP’ se refiere a un conjunto de subsistemas de software necesarios para alcanzar una solución global, en este caso configurar sitios web o servidores dinámicos con un esfuerzo reducido.

En las tecnologías LAMP esto se consigue mediante la unión de las siguientes tecnologías:

    Linux, el sistema operativo;
    Apache, el servidor web;
    MySQL, el gestor de bases de datos;
    Perl, PHP, o Python, los lenguajes de programación.

Ahora vamos a instalar los paquetes necesarios para tener un entorno LAMP.

**Apache**

  ``apt-get install apache2``

**MySQL**

  ``apt-get install mysql-server``

Durante la instalación del servicio se nos pedirá la contraseña del usuario ``root`` del servidor mysql.

Para acceder al servidor mysql::

  mysql -u root -p

Muestra las bases de datos::

  mysql>show databases; 

Usamos la base de datos indicadas::

  mysql>use nombre_base_datos; 

Muestra las tablas de esa base de datos::

  mysql>show tables; 

Muestra los campos de la tabla indicada::

  mysql>desc nombre_tabla; 

Muestra los registras de la tabla indicada::

  mysql>select * from nombre_tabla; 

Crea una base de datos con el nombre indicado::

  mysql>create database nombre_base_datos;

Crea un usuario con el nombre indicado::

  mysql>create user usuario; 

Da permiso a usuario con la contraseña indicada, para que maneje la base de datos indicada::

  mysql>GRANT ALL ON nombre_base_datos.* TO usuario IDENTIFIED BY 'contraseña_usuario'; 

**PHP5**

  ``apt-get install php5 libapache2-mod-php5 php5-mysql``

Para probar el funcionamiento de Apache y PHP es habitual crear un documento ``index.php`` en el directorio ``/var/www/html`` con el siguiente contenido::

    <html>
    <body>
      <? echo phpinfo(); ?>
    </body>
    </html>

Accede desde el navegador del cliente a ``http://www.iesgn.org/index.php``


Ejercicio: Instalación de un sistema LAMP

El acrónimo ‘LAMP’ se refiere a un conjunto de subsistemas de software necesarios para alcanzar una solución global, en este caso configurar sitios web o servidores dinámicos con un esfuerzo reducido.

En las tecnologías LAMP esto se consigue mediante la unión de las siguientes tecnologías:

    Linux, el sistema operativo;
    Apache, el servidor web;
    MySQL, el gestor de bases de datos;
    Perl, PHP, o Python, los lenguajes de programación.

Ahora vamos a instalar los paquetes necesarios para tener un entorno LAMP.
Apache

    apt-get install apache2

MySQL

    apt-get install mysql-server

Durante la instalación del servicio se nos pedirá la contraseña del usuario root del servidor mysql.

    Para acceder al servidor mysql:

      mysql -u root -p

    Muestra las bases de datos:

      mysql>show databases; 

    Usamos la base de datos indicadas:

      mysql>use nombre_base_datos; 

    Muestra las tablas de esa base de datos:

      mysql>show tables; 

    Muestra los campos de la tabla indicada:

      mysql>desc nombre_tabla; 

    Muestra los registras de la tabla indicada:

      mysql>select * from nombre_tabla; 

    Crea una base de datos con el nombre indicado:

      mysql>create database nombre_base_datos;

    Crea un usuario con el nombre indicado:

      mysql>create user usuario; 

    Da permiso a usuario con la contraseña indicada, para que maneje la base de datos indicada:

      mysql>GRANT ALL ON nombre_base_datos.* TO usuario IDENTIFIED BY 'contraseña_usuario'; 

PHP5

    apt-get install php5 libapache2-mod-php5 php5-mysql

Para probar el funcionamiento de Apache y PHP es habitual crear un documento index.php en el directorio /var/www/html con el siguiente contenido:

    <html>
    <body>
      <? echo phpinfo(); ?>
    </body>
    </html>

Accede desde el navegador del cliente a http://www.iesgn.org/index.php

