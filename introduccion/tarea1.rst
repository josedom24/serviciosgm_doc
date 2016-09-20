Este es el esquema de red con el que queremos trabajar. Vamos a utilizar VirualBox para simular las máquinas que necesitamos en nuestro esquema de trabajo, de esta forma necesitaremos 3 máquinas virtuales:

* **Servidor Windows Server**: Donde instalaremos Windows 2008 server. 
Un Cliente, donde se instalará Windows 7 
    Un cliente, donde se instalará Ubuntu


**El servidor Windows Server** tiene dos tarjetas virtuales de red:

* Una que hemos configurado modo puente, y que está configurada para que reciba la configuración en modo automático.
* Una que hemos configurado como "Red Interna", que configuramos de forma estática con las siguientes características:

**El cliente Windows** tiene una tarjeta de red, configurada en modo 'Red Interna' que debes configurar de forma estática.

**El cliente linux** tiene una tarjeta de red, configurada en modo 'Red Interna' que debes configurar de forma estática.



Dirección IP: 192.168.0.1.
Mascara de red: 255.255.255.0

Para que no tengamos problemas de conectividades vamos a desconectar el cortafuego del windows 2008, para ello:

	Inicio -> Herramientas administrativas -> Firewall de Windows con seguridad avanzada -> Y desactivamos los tres perfiles (dominio, privado, público),.


1) El servidor Windows 2008, lo primero es ponerle el nombre que hemos decidido:

Inicio -> Botón derecho en Equipo -> Propiedades -> Cambiar configuración -> Cambiar ...

 

 


4) En el cliente Windows 7 configuramos el nombre que hemos decidido.

5) El cliente Windows tiene una tarjeta de red, configurada en modo 'Red Interna' que debes configurar de forma estática, con la siguiente configuración:

IP: 192.168.0.2
Máscara: 255.255.255.0
Puerta de enlace: 192.168.0.1
Dns: 8.8.8.8

6) En el cliente Linux configuramos el nombre que hemos decidido.

7) El cliente linux tiene una tarjeta de red, configurada en modo 'Red Interna' que debes configurar de forma estática, con la siguiente configuración:

IP: 192.168.0.3
Máscara: 255.255.255.0
Puerta de enlace: 192.168.0.1
Dns: 8.8.8.8

8) Para terminar tenemos que hacer que el servidor Windows Server tenga la función de router y haga NAT, para que todas las peticiones que vengan por la "red Interna" sea enrutada por la tarjeta de red "Puente" y de esta manera los clientes sean capaz de salir a internet.

Para ello hay que seguir los siguientes pasos:

1. Incio -> Herramientas administrativas -> Administrador del servidor
2. Agregar roles -> Servicios de acceso y directiva de redes
3. En la pantalla servicios de rol escoge Enrutamiento -> Instalar
4. En administardor de servidor, en la ventana izquierda, desplegamo la pestañe de Roles, hasta que veamos Enrutamiento y acceso
5. Botón derecho -> Configurar y habilitar Enrutamiento y acceso remoto -> Traducción de direcciones de red (NAT) -> Siguiente -> Siguiente -> Configurar más adelante los servicios de nombres y direcciones




PRÁCTICA: INSTALACIÓN DE MÁQUINAS VIRTUALES





1) Vamos a crear una nueva máquina donde vamos a instalar el servidor con Windows 2008 Server:

    Pulsamos el botón "Nueva" para iniciar el asistente de creación de la máquina virtual.
    Le ponemos un nombre significativo y elegimos el tipo de sistema operativo: Windows 2008
    Asignamos la cantidad de memoria RAM de la máquina, le vamos a poner 512Mb si luego comprobamos que es pequeña la podemos aumentar.
    Creamos un nuevo disco virtual, del tipo de almacenamiento de expansión dinámica y un tamaño de 20 Gb.
    Configura en la sección "Almacenamiento" para que la unidad de CD/DVD se cargue con la imagen ISO de Windows 2008 Server aportada por el profesor.
    Configura las redes de esta máquina siguiendo las indicaciones del documento: Esquema de Red

Para entregar...

Entrega una captura de pantalla donde se vea la pantalla principal de VirtualBox con todas las características de la máquina que acabas de crear.


3) Instala Windows 2008 Server en la máquina que acabas de crear. Cuando finalices instala las "Guests Additions".

Para entregar...

Entrega una captura de pantalla donde se vea una ventana Windows donde se este ejecutando la máquina virtual creada y la ejecución en una ventana de comandos (cmd) del comando ipconfig para que se vea la configuración de red.


4) Crea dos nuevas máquinas virtuales para los clientes, con las siguientes características:

    Los discos duros virtuales deben de ser de almacenamiento de expansión dinámica, de 15 Gb de capacidad.
    La configuración de la red está explicada en el documento: Esquema de red
    La memoria RAM vamos a asignarla a 512Mb
    El profesor aporta las imágenes ISO de los discos de instalación de los sistemas operativos.

Para entregar...

Entrega dos capturas de pantalla: una donde se vea el cliente Windows con una consola de texto con el comando ipconfig ejecutado, de esta manera podremos ver la configuración de red, otra donde se vea el cliente Linux con una consola de comando donde se vea ejecutado la instrucción ifconfig, para ver la configuración de red.

Entrega dos capturas de pantalla de los clientes donde se vea que están navegando por internet.