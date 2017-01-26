Ejemplo fichero named.conf.local
================================

Un posible ejemplo de este fichero, donde se definen las zonas puede ser::

	zone "gonzalonazareno.org" {
        type master;
        file "db.gonzalonazareno";
	};

	zone "1.168.192.in-addr.arpa" {
        type master;
        file "db.192.168";
	};