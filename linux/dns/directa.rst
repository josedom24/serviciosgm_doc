Ejemplo de fichero de zona diracta: db.gonzalonazareno
======================================================

Un ejemplo de fichero de zona directa puede ser el siguiente::

	$TTL 86400      ; 1 day
	@                       IN SOA  papion.gonzalonazareno.org. postmaster.gonzalonazareno.org. (
	                                19423      ; serial
	                                21600      ; refresh (6 hours)
	                                3600       ; retry (1 hour)
	                                604800     ; expire (1 week)
	                                21600      ; minimum (6 hours)
	                                )
	@                      IN  NS      papion.gonzalonazareno.org.
	@                      IN  MX      10 mail.gonzalonazareno.org.	

	$ORIGIN gonzalonazareno.org.
	papion                  IN  A       192.168.3.4
	babuino                 IN  A       192.168.3.2
	correo                  IN  A       192.168.3.5
	dit                     IN  CNAME   papion