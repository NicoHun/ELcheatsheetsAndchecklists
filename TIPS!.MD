## Open poorten: ##

2 betekenissen!! 

    a) draait de service? 
    b) wordt deze geblokkeerd? 

A) is de enige juiste interpretatie.

B) kijk in uw firewall. Juiste naam: is de poort geblokkeerd of niet? (NIET: staat de poort open of niet)



Altijd makkelijk SSH'en in je VM:
klik op port forwarding en controleer de settings
Op Windows: gebruik putty en login via: 


ssh admin@127.0.0.1:2222



- ss vervangt netstat

- ss -tulnp


## nmap ##

Van buitenaf je poorten scannen.

`nmap -A -T4 192.168.56.14`

TCPSYN en daarna TCPACK (nmap doet de ACK niet)

ERROR 404 : dan zit je al op Applicatielaag (want als de rest niet zou kloppen, 
dan kun je deze fout nog niet eens krijgen.)


IN 't voorbeeld: hij ziet zelfs de versie van OpenSSH (dus je kunt beginnen zoeken naar exploits die gevoelig 
zijn aan die versie ;-))

## FILESERVER ##

nmblookup

##LOGS ##

journalctl -f -u httpd.service <br>
(-f betekent dat hij blijft openstaan)

**/var/log/httpd/***


## Firewall: ##

2 manieren

        - pakketje weggooien en negeren
        - pakketje weggooien en reageren

## Bash-completion installeren ##
--> deze is nog completer dan de ingebouwde (omdat deze ook opties voorstelt)
