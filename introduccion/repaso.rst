Repaso de redes
===============

Configuración TCP/IP
--------------------

La mayoría de personas ya saben que para que los PCs de una red puedan comunicarse entre sí, deben disponer de una dirección IP y de una máscara de subred. Además, si queremos que disponga de conexión a Internet, es necesario configurar la dirección IP de la puerta de enlace y la dirección IP de dos servidores DNS.

.. image:: img/repaso1.png

Dentro de una misma red, los PCs deben tener una dirección IP perteneciente al rango 
de dicha red. Si el rango es desde 192.168.0.0 hasta 192.168.0.255, las IPs de los PCs deberán tener los tres primeros números iguales (192.168.0.X) y el último número podrá cambiar desde 1 hasta 254, porque no se permite la utilización de la primera ni de la última dirección IP del rango ya que quedan reservadas.

Cada PC deberá tener una dirección IP diferente. Si dos PCs tienen la misma IP, habrá un conflicto de IP y ninguno de ellos podrá comunicarse hasta que no se resuelva el conflicto cambiando la IP a uno de ellos. Si no sabemos qué IP poner, podemos ver la IP de otro PC de nuestra red en el que funcione correctamente la conexión de Internet y por regla general, cambiar el último valor por otro diferente que no tenga ningún otro PC.

* La **Máscara de subred** determina el número de PCs del rango. Casi siempre se suele  utilizar la máscara 255.255.255.0 que corresponde a un rango de 256 direcciones IP (suficientes para casi todos los centros educativos) en los que todos los PCs tienen los tres primeros números de la IP iguales y solo cambia el último. Lo normal es que todos  los PCs de nuestra red tengan configurada la misma máscara de subred. Si no sabemos cual es la máscara de subred, podemos verla en otro PC que funcione correctamente la conexión de Internet.

* La **Puerta de enlace** deberá ser una IP del rango ya que de lo contrario, nuestro PC no será capaz de comunicarse con ella y no tendrá acceso a Internet. Lo normal es que todos los PCs de nuestra red tengan configurada la misma puerta de enlace. Si no sabemos la IP de nuestra puerta de enlace, podemos verla en otro PC que funcione correctamente la conexión de Internet.

* Los **DNS preferido y alternativo** nos los debe proporcionar la compañía que presta el servicio. Telefónica usa el 80.58.0.33 y el 80.58.32.97. Lo normal es que todos los PCs de nuestra red tengan configurados los mismos DNSs. Si no sabemos la IP de los DNS preferido y alternativo, podemos verlos en otro PC que funcione correctamente la conexión de Internet.