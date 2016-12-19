Ejercicio: Instalación y configuración de un servidor dhcp en linux
===================================================================

Después de leer la documentación, instala el servidor dhcp. Recuerda que al inicializar el servicio nos dará un error, esto es debido a que no hemos configurado el servidor.

**Instalación del servidor isc-dhcp-server**

Para instalar nuestro servidor dhcp ejecutamos::

	apt-get install isc-dhcp-server

.. note::

	Cuando instalamos el servidor por primera se produce un error, ya que no está configurado. Puedes ver los errores producidos por el servidor en el fichero ``/var/log/syslog``.


**Configuración del servidor isc-dhcp-server**

Lo primero que tenemos que hacer es configurar el interfaz de red por el que va a trabajar el servidor dhcp, para ello editamos el siguiente fichero::

	/etc/default/isc-dhcp-server

Donde configuramos el parámetro interfaces, por ejemplo::

	INTERFACES="eth1"

El fichero principal de configuración de DHCP es::

	/etc/dhcp/dhcpd.conf

El fichero de configuración está dividido en dos partes:

    * Parte principal (valores por defecto): especifica los parámetros generales que definen la concesión y los parámetros adicionales que se proporcionarán al cliente.
    * Secciones (concretan a la principal):
        * Subnet: Especifican rangos de direcciones IPs que serán cedidas a los clientes que lo soliciten.
        * Host: Especificaciones concretas de equipos.

En la parte principal podemos configurar los siguientes parámetros, que más tarde podremos reescribir en las distintas secciones:

    * ``max-lease-time``: Tiempo de la concesión de la dirección IP
    * ``default-lease-time``: Tiempo de renovación de la concesión
    * ``option routers``: Indicamos la dirección red de la puerta de enlace que se utiliza para salir a internet.
    * ``option domain-name-server``: Se pone las direcciones IP de los servidores DNS que va a utilizar el cliente.
    * ``option domain­-name``: Nombre del dominio que se manda al cliente.
    * ``option subnet­mask``: Subred enviada a los clientes.
    * ``option broadcast-­address``: Dirección de difusión de la red.

Al indicar una sección subnet tenemos que indicar la dirección de la red y la mascara de red y entre llaves podemos poner los siguientes parámetros:

    * ``range``: Indicamos el rango de direcciones IP que vamos a asignar.
    * Alguno de los parámetros que hemos explicado en la sección principal.

Ejemplo de configuración de la sección subnet puede ser::

	subnet 192.168.0.0 netmask 255.255.255.0 {
	  range 192.168.0.60 192.168.0.90;
	  option routers 192.168.0.254;
	  option domain-­nam-e­servers 80.58.0.33, 80.58.32.9;
	}

Reinciciamos el servidor dhcp::

	systemctl restart isc-dhcp-server

Sólo falta configurar los clientes para que tomen la configuración de red de forma dinámica.

.. note::

	En Windows la instrucción ``ipconfig /release`` libera la concesión, la instrucción ``ipconfig /renew`` la renueva. En linux el comando para liberar la concesión es ``dhclient -r`` y el que nos permite renovarla será ``dhclient``.

.. warning::

	**Ejercicios**

	1. Configura el servidor dhcp con las siguientes características:

	    * Rango de direcciones a repartir: 192.168.0.100 - 192.168.0.110
	    * Máscara de red: 255.255.255.0
	    * Duración de la concesión: 1 hora
	    * Puerta de enlace: 192.168.0.1
	    * Servidores DNS: 192.168.102.2

	2. Configura los clientes para obtener direccionamiento dinámico. Comprueba las configuraciones de red que han tomado los clientes. Visualiza el fichero del servidor donde se guarda las configuraciones asignadas.

