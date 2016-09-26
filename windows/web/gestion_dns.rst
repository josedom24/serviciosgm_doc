Gestión de DNS externo
======================

En este momento tenemos un servidor web con un sitio web y queremos que sea accesible desde el exterior, ¿qué nos falta? pues la configuración de un servidor DNS externo con un nombre de dominio dirigido en todo momento a nuestra dirección IP pública. Dependiendo del tipo de acceso a Internet que tengamos y si tenemos o no previamente un nombre de dominio registrado pueden darse los siguientes casos:

	* Tenemos dirección IP pública estática y un nombre de dominio registrado y apuntando a nuestra dirección IP pública: Este es el caso ideal y no necesitaríamos configurar nada.
	* Tenemos dirección IP pública estática y no tenemos un nombre de dominio registrado: Recomendamos utilizar dyndns.com o cualquier servicio similar que nos permita almacenar un registro DNS gratuito.
	* Tenemos una dirección IP dinámica y un nombre de dominio registrado: Utilizamos la aplicación que nos proporcione la empresa en la que tenemos registrado el dominio para actualizar el registro DNS cada vez que cambie la dirección IP
	* Tenemos dirección IP dinámica y no tenemos registrado un nombre de dominio: Seguramente el caso más habitual, entonces recomendamos utilizar dyndns.com, que es un servicio gratuito de gestión de nombres de dominios, aunque puede utilizarse cualquier otro si así se prefiere.

La mayoría de los servicios ADSL que tenemos contratado usan dhcp para asignarnos una dirección IP a nuestro router. Cuando apagamos y encendemos de nuevo el router obtenemos otra dirección IP y debemos actualizar el DNS externo de dyndns para que al acceder a nuestro nombre de dominio se acceda a la IP correcta. Normalmente se utiliza un programa que no os ofrece el servicio que hace esta tarea de forma automática.