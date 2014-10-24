## Open poorten: ##

2 betekenissen!! 
    a) draait de service? 
    b) wordt ie geblokkeerd? 

A) is de enige juiste interpretatie.

B) kijk in je firewall, he. Juiste naam: is de poort geblokkeerd of niet? (NIET: staat de poort open of niet)



Altijd makkelijk SSH'en in je VM:
klik op port forwarding en controleer de settings
Op Windows: gebruik putty en login via: 


ssh admin@127.0.0.1:2222




- ss vervangt netstat
ss -tulnp


## nmap ##

Van buitenaf je poorten scannen.

`nmap -A -T4 192.168.56.14`

TCPSYN en daarna TCPACK (nmap doet de ACK niet)

IN 't voorbeeld: hij ziet zelfs de versie van OpenSSH (dus je kunt beginnen zoeken naar exploits die gevoelig 
zijn aan die versie ;-))

## FILESERVER ##

nmblookup

##LOGS ##

journalctl -f -u httpd.service <br>
(-f betekent dat hij blijft openstaan)


