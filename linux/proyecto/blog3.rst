Blog 3: Instalación y configuración de un servidor Web
======================================================

Una de los principales servicios que va a ofrecer nuestro servidor es una página web con las siguientes características:

    * Tienes que escoger un nombre de dominio que vas a utilizar (elije un nombre según el nombre del instituto), para este documento voy a utilizar ``dominio.com``.
    * La página principal del insituto será ``www.dominio.com`` donde podrás encontrar información y noticias sobre el instituto (utiliza una plantilla modificada con el nombre del insitituto para que parezca una página real).
    * La página ``www.dominio.com/documentos``, muestra una lista con toda la documentación pública del instituto. Toda esta documentación estará en el directorio ``/srv/doc``.
    * Cada profesor tiene un usuario en el servidor, además existen usuarios especiales: director, jefeestudios, secretario,...
    * La página ``www.dominio.com/profesores``, es una zona privada donde tienen accesos todos los usuarios, sin embargo a la página ``www.dominio.com/equipodirectivo`` sólo tienen accesos los usuarios del equipo directivo: director, jefeestudios, secretario,...
    * Cada uno de los profesores puede gestionar su propia página web, para ello activa el módulo ``mod_userdir``.
    *^El departamento de informática posee una página web realizada con moodle, que se accede en ``informatica.dominio.com``.

.. warning::

    1. Explica la instalación del servidor web.
    2. Se valorará positivamente la plantilla escogida y la modificación que se haga para que parezca una página real. Utiliza la misma plantilla para todas las páginas del sitio.
    3. Explica como has configurado el servidor para mostrar la página ``www.dominio.com/documentos``.
    4. Autentificación: Explica como se crean los usuarios y cómo se configura las distintas páginas (``www.dominio.com/profesores``, ``www.dominio.com/equipodirectivo``) para configurar la autentificación.
    5. Invenstiga como activar el ``módulo mod_userdir``, ¿para qué sirve? Pon algún ejemplo para comprobar el funcionamiento.
    6. Explica la instalación de un servidor LAMP.
    7. Realiza una pequeña guía (no hace falta poner capturas de pantalla) de instalación de moodle. También tienes que explicar la configuración del nuevo virtual host.

