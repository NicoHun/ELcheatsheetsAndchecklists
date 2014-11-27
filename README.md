EL Cheatsheets and checklists
=============================

Cheat sheets en checklists ivm Enterprise Linux

## Git (Bitbucket & GitHub)

Hoewel je veel met aliases werkt, toch enkele commands voor mocht je je eigen niet ter beschikking hebben.

| Actie                                  | Command                                    |
| :---                                    | :---                                       |
| Alles toevoegen om te committen                | `git add -A` |
| Commit 1 specifiek lokaal gewijzigd bestand  | `git add [Tab]`                       |
| Check of er verschillen zijn tussen de online-versie en jouw lokale versie | `git status`                         |
| Haal alle wijzigingen binnen van de online-versie  | `git pull`                       |



## Vagrant

| Actie                                  | Command                                    |
| :---                                    | :---                                       |
| Vagrant initialiseren                | `vagrant init .../box` |
| Vagrant opzetten en booten | `vagrant up (evt. naam host toevoegen)`                         |
| Vagrant box herladen (voor niet al te ingrijpende wijzigingen)  | `vagrant reload (evt. naam host toevoegen)`                       |
| Vagrant box verwijderen en opnieuw opzetten in 1 handeling (wnnr ingrijpende wijzigingen)  | `vagrant destroy && up (evt. naam host toevoegen)`                       |
| Vagrant ssh'en                | `vagrant ssh (naam VM)` |
| Vagrant status krijgen                | `vagrant status (evt. naam host)` |

##Troubleshooting tips ##

* repoquery -qf */netstat */lsof */nmap
      * Wanneer niet geïnstalleerd: yum install yum-utils
* Yum install net-tools
* IP-conflicten opsporen: `sudo yum install arp-scan`
<br> en 
    `arp-scan -I eth0 -l`

* In plaats van ifconfig, NU _ip add_ / _ip address_
* Ip adressen zelf aanpassen: vi /etc/sysconfig/network-scripts/ifcfg-eth0
* ping -c 5 [ip address]

* lspci (al de PCI-bussen en apparaten van het systeem)
* lsppci -n (identificatiecodes: laatste kolom cijfers en letters geven _Fabrikant:type apparaat_ weer )
* ~= >> 
    hwinfo
* lsof -i -n -P | grep ... ( list open files, geeft lijst geopende bestanden en door welke processen deze gebruikt worden, weer) 
<br>Opties:
      * -i: sockets
      * -n: gebruik geen DNS
      * -P: toon poortnummers
* arp [Adress Resolution Protocol config](http://xmodulo.com/how-to-add-or-remove-static-arp-entry-on-linux.html)
* Default gateway: 
    * netstat -rn
    * route -n
* DNS: /etc/resolv.conf

* Service is depricated, gebruik in de plaats:
    * _systemctl_ start httpd.service
    * systemctl status httpd.service
    * systemctl enable httpd.service
    * systemctl disable httpd.service
* top
* ps | grep [naam_service]
* Firewall: /etc/sysconfig/iptables
    * systemctl restart iptables.service
* tailof `less` /var/logs/messages
      * (en verdere logs in de directory logs)
      * zoek dan naar DHCP op deze manier: /DHCP
* _yum install nmap_...
* nmap -p ftp,http*

* Vergeet niet de service 'remote' te testen (op je host-machine)
