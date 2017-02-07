Ejemplo de fichero de zona inversa: db.192.168
==============================================

Un ejemplo de fichero de zona inversa puede ser el siguiente::

	$TTL 86400      ; 1 day
	@                    IN SOA  papion.gonzaloanzareno.org. postmaster.gonzalonazareno.org. (
	                                12998      ; serial
	                                21600      ; refresh (6 hours)
	                                3600       ; retry (1 hour)
	                                604800     ; expire (1 week)
	                                21600      ; minimum (6 hours)
	                                )
	@                    IN NS      papion.gonzalonazareno.org.	
	
	$ORIGIN 1.168.192.in-addr.arpa.
	4                    IN PTR     papion.gonzalonazareno.org.
	2                    IN PTR     babuino.gonzalonazareno.org.
	5                    IN PTR     correo.gonzalonazareno.org.
