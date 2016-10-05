Entrega 3
=========

Servidor DNS
------------

Actualmente la resolución de nombres se está haciendo de forma estática. Es necesario la instalación y configuración de un servidor DNS en nuestro servidor Windows Server 2008 que le permita a todos los clientes poder resolver los nombres de nuestro dominio ``masterlan.com``.

.. note::

	 Es necesario que borres todos las resoluciones que habías indicado en los ficheros hosts de los clientes.

Instala un servidor DNS con las siguientes características:

* El servidor DNS, que está en el servidor Windows 2008, se llama ``nombredelservidor*.masterlan.com``
* Vamos a suponer que existe un servidor de correos, en la dirección 10.0.0.100, se llama ``mail.masterlan.com``
* Se debe conocer las direcciones de las dos páginas webs: ``www.masterlan.com`` y ``direccion.masterlan.com``.
* Se debe conocer el nombre de la dirección ip del servidor.

Configura el servidor DNS de manera adecuada, y modifica el servidor DHCP para mandar a los clientes como DNS la dirección del servidor.

.. warning::

	**Entregar...**

	1. Escribe una pequeña guía de como se instala el servidor DNS. Indica las ventajas de tener instalado un servidor DNS en una intranet.
	2. Indica el cambio que hay que hacer en el servidor dhcp para que el sistema funcione de manera adecuada.
	3. Vuelve a asignar de forma dinámica la configuración de red a los clientes, y haz una prueba de funcionamiento accediendo a alguna de las páginas web de masterlan.com y accediendo a alguna otra página web.
	4. Para comprobar el funcionamiento, copia las salidas de los comandos nslookup/dig 

		* Servidor DNS de masterlan.com 
		* Dirección ip de www.masterlan.com
		* Servidor de correo que obtiene los correos enviados a masterlan.com 
		* Nombre de la dirección 10.0.0.1
		* Dirección IP de www.josedomingo.org
