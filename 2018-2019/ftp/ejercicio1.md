# Ejercicio: Instalación del servidor proFTPd autentificado

El objetivo de esta práctica es que los usuarios locales del equipo puedan acceder a sus directorios por medio del servidor FTP.

Para ello sigue los siguiente pasos:

1. Crea dos usuarios locales: Jose y Maria. (Recuerda que para crear usuario utiliza la instrucción `adduser`)

2. Instala y configura el servidor proFTPd para que los usuarios puedan acceder a sus directorios personales:

 	    apt-get install proftpd

El fichero de configuración es ``/etc/proftpd/proftpd.conf``, en este fichero descomenta la línea ``DefaultRoot`` para que los usuario no puedan salir de su directorio. Por último reinicia el servicio.

Accede a ``ftp.iesgn.org``, comprueba que tienes que autentificarte y comprueba el acceso con los dos usuarios. (Debes configurar el servidor DNS para que desde el cliente puedas acceder a ese nombre de máquina).

### Ejercicios
	
1. Realiza las configuraciones necesarias para configurar un ftp autentificado.
2. Accede desde el cliente ftp desde linux y windows

