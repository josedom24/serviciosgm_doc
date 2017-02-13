Blog 8: Instalación y configuración del acceso remoto
=====================================================

Para facilitar la administración por parte de los técnicos de los clientes linux vamos a configurar el sistema para que se pueda acceder remotamente de dos formas:

* Por seguridad se va a realizar la conexión utilizando el puerto 2222.
* SSH con claves públicas: Desde el servidor, el administrador del sistema va a poder acceder a los clientes linux mediante ssh con clave pública, por lo que no será necerario que introduzca la contraseña.
* Escritorio remoto con VNC: Se puede acceder con un cliente de escritorio remoto a los clientes linux, pero es necesario poner una contraseña de acceso, qué sólo saben los técnicos.

.. warning::

    1. Escribe un manual donde expliques la configuración necesaria para que se pueda acceder a una máquina por ssh utilizando clave pública, por el puerto 2222.
    2. Muestra la configuración en linux para permitir el acceso remoto por VNC, y muestra algunas capturas de pantalla (con Windows y Linux) accediendo por escritorio remoto.
