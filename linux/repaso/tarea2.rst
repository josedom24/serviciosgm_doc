Tarea 2: Niveles de ejecución. Arranque y parada de los servicios
=================================================================

**Niveles de ejecución**

Los niveles de ejecución ( Run Levels ) definen diferentes estados de funcionamiento de un Sistema Linux::

    0 Parada del sistema
    1 Modo monousuario
    2 Modo multiusuario
    3 Modo multiusuario
    4 No usado
    5 Modo multiusuario
    6 Parada y arranque
    7-9 No se usan

**Secuencia de arranque**

*1) Debian arranca ejecutando el programa ``init``. El archivo de configuración de init es ``/etc/inittab``.*

La entrada ``initdefault`` determina el nivel de ejecución inicial del sistema.

.. note::

    Ejercicios

    1. Edita el fichero ``/etc/inittab``, localiza la entrada ``initdefault``, y determina en que nivel de ejecución está trabajando el sistema.
    2. También puedes obtener el nivel de ejecución actual ejecutando la instrucción ``runlevel``.

*2) Los primeros scripts que se ejecutan a continuación (indicado en la linea del fichero ``/etc/inittab: si::sysinit:/etc/init.d/rcS``) son los que se encuentra en el directorio ``/etc/rcS``.*

Estos scripts son los encargados de realizar algunas tareas como:

    * Monta el file system root y /proc.
    * Elimina temporales y archivos de bloqueo.
    * Establece el reloj
    * Inicia scripts de red y activa la partición swap.
    * Activa el teclado y fuentes.
    * Carga módulos.
    * Establece valores a muchas variables del entorno:PATH, HOSTNAME,…
    * Arranca la swap
    * Arranca fsck automático, si hace falta.
    * Activa quotas.
    * Chequea los argumentos pasados al kernel.
    * Chequea los filesystems
    * Inicializa los puertos serie.
    * Puertos USB.

.. note::

    Ejercicios

    3. Lista los ficheros que se encuentran en el directorio ``/etc/rcS.d``.
    4. Comprueba que son enlaces simbólicos a los scripts que se encuentran en el directorio ``/etc/init.d``.

*3)  A continuación se ejecutan los scripts de inicialización de los servicios del nivel de ejecución por defecto.*

Estos scripts se encuentran en los directorios ``/etc/rcn`` donde n es el nivel de ejecución.

Ejemplo::

    Nivel Script Directorio
    0      rc 0  /etc/rc0.d/
    1      rc 1  /etc/rc1.d/
    2      rc 2  /etc/rc2.d/
    3      rc 3  /etc/rc3.d/

Es el script ``/etc/init.d/rc`` el que procesa todos los archivos K y S de los directorios ``/etc/rcn.d``

    * Para ( con el argumento stop ) aquellos procesos que comienzan por K ( kill )
    * Lanza ( con el argumento start ) los que comienzan por S ( start ).
    * Después de la letra S o K hay dos dígitos numéricos que indican el orden de ejecución. El orden es ASCII.
    * Todos los ficheros K o S son enlaces simbólicos a los scrips de cada servicio que están en el directorio /etc/init.d

.. note::

    Ejercicios

    5. Visualiza los ficheros de los distintos directorios ``/etc/rcn.d``.
    6. Comprueba los ficheros de ejecución del nivel de ejecución que se ejecuta por defecto en Debian.
    7. Con la instrucción ``telinit`` podemos ejecutar otros niveles de ejecución. Entra en el nivel monousuario. Entra en el nivel de reinicio. Entra en el nivel de parada del sistema.

De modo esquemático podemos ver:

.. image:: https://github.com/josedom24/serviciosgm_doc/raw/master/linux/repaso/img/niveles.png

*4) ¿Qué hacer para eliminar un servicio en un determinado nivel?*

    * Borrar el vínculo simbólico en ``/etc/rcn.d/``
    * Renombrarlo con algo que no empiece con S o K y dejarlo por si queremos luego activarlo.
    * Lo que no hay que hacer nunca es eliminar el archivo original en ``/etc/init.d/``

.. note::

    Ejercicios  

    8. Vamos a eliminar el servicio ``gdm3`` (encargado de iniciar el servidor gráfico) del nivel de ejecución 2, para ello elimina el fichero que inicia ese servicio. 
    9. Reinica el sistema y comprueba que el servidor gráfico no se ha iniciado.    
    10. Para restablecer el enlace simbólico para que podamos iniciar el servicio usamos la instrucción ``update-rc.d`` (busca la página del manual para aprender más sobre esta instrucción. Ejecuta:
    ``update-rc.d gdm defaults`` para crear los enlaces simbólicos que ejecutan el script de gdm    
    11. Vuelve a reiniciar el sistema y comprueba que el servidor gráfico se vuelve a ejecutar. 
    12. Pregunta: ¿Para qué podríamos utilizar la configuración de distintos niveles de ejecución?  

**Arranque y parada de lo servicios**

Una vez que se han cargado los servicios que se encuentran en el directorio ``/etc/rc2.d``, podemos comprobar que los demonios correspondientes a cada servicio se están ejecutando con la instrucción::

    ps -A

En cualquier momento podemos parar o reiniciar cualquier servicio ejecutando los scripts del directorio ``/etc/init.d`` con las siguientes opciones: start, stop, restart, force-reload,...

También se puede utilizar el comando ``service``, de esta forma para reiniciar el servicio ssh podemos ejecutar dos comandos::

    /etc/init.d/ssh restart
    service ssh restart

.. note::

    Ejercicios  

    13. Comprueba que el servicio ``ssh`` se está ejecutando.   
    14. Para el servicio, y comprueba con la instrucción ps que el proceso no se está ejecutando.   
    15. Vuelve a reiniciar el servicio.

**Envío de señales a los procesos**

Es posible el envío de distintas señales a los procesos. La más usada es matar un proceso, si por ejemplo se queda inactivo. Para ello utilizamos la siguiente instrucción::

    kill -9 PID

El PID es el identificador del proceso, y lo puedes obtener mirando la lista de procesos por ejemplo con ``ps -A``.

Podemos también utilizar la siguiente instrucción::

    killall nombredelproceso

Del mismo modo puedes ver el nombre del proceso mirando la lista de procesos con ``ps``.

.. note::

    Ejercicios

    16. Imagínate que el servidor gráfico se queda “colgado”. Entra en un terminal de texto con CTRL+ALT+F1, y tras iniciar sesión como root mata el proceso gdm (Gestor de arranque del servidor gráfico).
    17. Para comprobar que el servidor gráfico no funciona puedes hacer varias cosas: lista los procesos y comprueba que no existe el proceso gdm ni el Xorg. También puedes intentar entrar en la consola gráfica con CTRL+ALT+F7.
    18. Vuelve a ejecutar el gestor de arranque gráfico gdm.
    19. Del mismo modo puedes matar el demonio del servicio ssh, y volver a reiniciarlo posteriormente.

**Systemd**

Debian, tomó la importante decisión de adoptar Systemd como su próximo sistema de inicio GNU/Linux. Systemd ha sido diseñado para ofrecer un arranque más rápido, más seguro y sobre todo más flexible que SysV. Permite el arranque en paralelo de servicios y su inicio en función de la activación externa, en vez de un arranque lineal y en función de modos de ejecución fijos propio de SysV que han quedado obsoletos.

*¿Dónde están los archivos de systemd?*

En ``/etc/systemd/system/``  y sus subdirectorios, podemos encontrar los archivos de los servicios activos (*nombre.de.servicio.service*), que son enlaces simbólicos a los archivos de servicios alojados en ``/usr/lib/systemd/system/``. Así, en ``/etc/systemd/system/`` y sus subdirectorios podemos encontrar, entre otros, por ejemplo::

    sshd.service -> /lib/systemd/system/ssh.service

*¿Cómo se controlan los servicios en Systemd?*

Para saber qué servicios están activos (lista todos los servicios e informa de si están cargados, activos, montados, en espera, etc)::

    systemctl list-units --type=service

Arrancar un servicio (por ejemplo para arrancar el servidor web)::

    systemctl start apache2    

Detener un servicio (detiene el servicio de impresión CUPS)::

    systemctl stop cups    

Apagar y reiniciar un servicio::

    systemctl restart cups

Apagar y reiniciar un servicio de forma "suave": (vuelve a cargar su archivo de configuración antes de arrancarlo)::

    systemctl reload cups    

Ver el estado de un servicio::

    systemctl status cups

Para hacer que un servicio se inicie al arrancar el ordenador (hará que Samba se incicie al arranque del ordenador)::

    systemctl enable smbd     

Podemos desactivarlo en el arranque de la siguiente manera::

    systemctl disable smbd   

Podemos observar que la orden ``systemctl enable smbd``, lo que hará será crear el enlace simbólico en ``/etc/systemd/system/``, que apunte al servicio ``smbd.service`` que reside en ``/usr/lib/systemd/system/``, de forma que Systemd active el servicio Samba en el próximo arranque del sistema.

**Targets**

systemd utiliza targets («objetivos») que sirven a un propósito similar a los runlevels («niveles de ejecución»), pero que tienen un comportamiento un poco diferente. Cada target se nomina, en lugar de numerarse, y está destinado a servir a un propósito específico con la posibilidad de realizar más de una acción al mismo tiempo. Algunos targets son activados heredando todos los servicios de otro target e implementando servicios adicionales. 

La correspondencia entre runlevels y targets es la siguiente:

================    =====================================================   ===================================================================================================================================
Runlevel de SysV    Target de systemd                                       Notas
================    =====================================================   ===================================================================================================================================
0                   runlevel0.target, poweroff.target                       Detiene el sistema.
1, s, single        runlevel1.target, rescue.target                         Modalidad de usuario único.
2, 4                runlevel2.target, runlevel4.target, multi-user.target   Definidos por el usuario. Preconfigurados a 3.
3                   runlevel3.target, multi-user.target                     Multiusuario, no gráfica. Los usuarios, por lo general, pueden acceder a través de múltiples consolas o a través de la red.
5                   runlevel5.target, graphical.target                      Multiusuario, gráfica. Por lo general, tiene todos los servicios del nivel de ejecución 3, además de un inicio de sesión gráfica.
6                   runlevel6.target, reboot.target                         Reinicia el sistema.
emergency           emergency.target    Consola de emergencia. 
================    =====================================================   ===================================================================================================================================

Para saber los targets que están cargados::

    systemctl list-units --type=target

Para cambiar de un target a otro, por ejemplo para reiniciar el sistema podemos ejecutar::

    systemctl isolate reboot.target

**Logs de procesos**

Los logs de los procesos se guardan en el directorio ``/var/log/``, por ejemplo el fichero syslog es el principal, y en él podemos encontrar mensajes de distintos procesos (por ejemplo el servidor dhcp). Algunos servicios tienen su propio fichero de log, por ejemplo ``/var/log/apache2/error.log``.

Normalmente para ver la últimas líneas del fichero de log, utilizamos el siguiente comando::

    tailf /var/log/syslog

Con systemd tenemos otra manera de ver los logs, si al iniciar un servicio nos da un error, podemos ver los mensajes del log con la instrucción::

    journalctl -xn

.. note::

    Ejercicios  

    20. Para el servicio ``ssh``, con systemd.  
    21. Modifica el fichero de configuración del servidor ``/etc/ssh/sshd_config``, borra alguna letra para que se produzca un error al inciar el servicio. Inicia el servidor con systemd y comprueba que hay un error.    
    22. Ejecuta la instrucción adecuada para ver el error que se ha producido.  
    23. Arregla el fichero de configuración y vuelve a iniciar el servicio.
