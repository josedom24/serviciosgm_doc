Tarea: Consultas DNS con dig
============================

dig es una herramienta que permite hacer consultas a un servidor DNS desde la línea de comandos, es el sustituto de los programas nslookup y host. La sintaxis es::

    dig [-t tipo de registro] [@servidor DNS] Consulta DNS

El tipo de registro por defecto es ADDRESS y el servidor DNS por defecto el definido en /etc/resolv.conf.

Nota: si no funciona el comndo dig, instala el paquete dnsutils que lo incluye.

1. Preguntas a registros del tipo A: Obtén la dirección ip de los siguientes dominios::

    www.gonzalonazareno.org 
    www.eltiempo.es
    www.us.es
    es.wikipedia.org
    www.ubuntu.com

2. Preguntas a registros tipo NS: Obtén la dirección y los servidor DNS que corresponden a los siguientes dominios::

	dominio raíz
	com
	org
	es
	us.es
	wikipedia.org
	ubuntu.com

3. Preguntas a registros MX: Obtén el nombre y la dirección del ordenador al que se mandan los correos que se envían a los siguientes dominios::

    gonzalonazareno.org
    us.es
    wikipedia.org
    ubuntu.com

4. ¿Qué tipo de registro es el que resuelve las siguientes direcciones::
         
    www.josedomingo.org
    informatica.gonzalonazareno.org

Indica el nombre canónico de las máquinas a las que corresponden.

5. Comprueba la dirección ip y el servidor DNS asociado a ``dit.gonzalonazareno.org``, desde dentro de la intranet del ciclo formativo y desde fuera. ¿Cuáles son las diferencias? ¿A qué crees que es debido?

6. Pregunta sobre resolución inversa: En clase, ¿a qué nombre corresponde la dirección ip ``172.22.0.1``?