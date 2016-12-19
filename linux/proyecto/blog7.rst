Blog 7: Instalación y configuración de un servidor DNS
======================================================

Queremos centralizar la gestión de los nombres de las máquinas de nuestro dominio instalando un DNS en nuestro servidor, además podremos conseguir aumentar la velocidad de navegación de nuestros clientes. Para ello vamos a instalar en nuestro servidor debian un servidor DNS bind9 con las siguientes características:

    * Tiene que tener configurada una zona de resolución directa y otra zona de resolución inversa.
    * Todos los clientes deben utilizar este servidor DNS para realizar la resolución de nombres.

..warning::

    1. Explica razonadamente la afirmación: *"instalando un DNS en nuestro servidor, además podremos conseguir aumentar la velocidad de navegación de nuestros clientes"*.
    2. Explica cómo se instala el servidor DNS y configura el servidor de manera adecuada, muestra los archivos necesarios tras la configuración. Debes decidir, teniendo en cuenta el punto anterior, los nombres que debe resolver el servidor (el cliente que tiene hecha la reserva DHCP también se debe resolver).
    3. ¿Qué modificación debes hacer en el servidor DHCP para qué los clientes utilicen el servidor DNS?
    4. Muestra desde los clientes, las consultas dns hechas con dig y nslookup que respondan:

        * Servidor dns de ``dominio.com``.
        * Dirección ip de ``informatica.dominio.com``.
        * Nombre de la dirección ip del servidor (resolución inversa).
        * Dirección ip de ``www.josedomingo.org``.
