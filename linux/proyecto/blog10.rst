Blog 10: Instalación y configuración del servidor de correos
============================================================


Queremos ofrecer en nuestro sistema el servicio de correo electrónico para permitir que los usuarios del servidor puedan mandarse correos. Para ello vamos a instalar un servidor postfix. Nuestro sistema de correos tendrá las siguientes características:

* Crearemos un nuevo nombre ``smtp.dominio.com`` que será el servidor de correos saliente.
* Crearemos un servidor ``mail.dominio.com`` que será un servidor de correo pop.
* Los usuarios tendrán en sus ordenadores clientes de correo que podrán utilizar usando los dos servidores anteriores.
* Además usando el protocolo imap, y un cliente web de correos (squirredmail) podrán gestionar sus correos desde la URL ``correo.dominio.com``

.. warning::

    1. Describe la instalación y configuración del servidor postfix.
    2. Muestra una prueba de envío y recepción de correo desde el servidor usando el comando mail. Muestra también la salida del log.
    3. Explica la instalación y configuración del servidor pop e imap.
    4. Muestra la configuración del cliente de correos (servidor de correo saliente y servidor de correos pop).
    5. Explica la instalación de squirrelmail y la configuración necesaria para que se pueda acceder desde la URL indicada anteriormente.
    6. Con captura de pantalla demuestra el envío de un correo desde el squirredmail y la recepción por parte del usuario destinatario usando un cliente de correos.
