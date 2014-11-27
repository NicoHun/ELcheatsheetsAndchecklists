EL Cheatsheets and checklists - Nico Hunink (3 TIN HoGent)
=============================

Cheat sheets en checklists ivm olod Enterprise Linux

## Git (Bitbucket & GitHub)

Hoewel je veel met aliases werkt, toch enkele commands voor mocht je je eigen niet ter beschikking hebben.

| Actie                                  | Command                                    |
| :---                                    | :---                                       |
| Alles toevoegen om te committen                | `git add -A` |
| Commit 1 specifiek lokaal gewijzigd bestand  | `git add [Tab]`        |
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

### Tools ### 
* `yum install setroubleshoot`, gevolgd door: `restart auditd`
* `journalctl`
* `repoquery -qf */netstat */lsof */nmap`
      * Wanneer niet geïnstalleerd: `yum install yum-utils`
* `Yum install net-tools`
* IP-conflicten opsporen: `sudo yum install arp-scan`
<br> en 
    `arp-scan -I eth0 -l`
* _yum install nmap_

###SELinux ###

| Actie                                  | Command                                    |
| :---                                    | :---                                       |
| Status controleren                | `sestatus` |
| Starten setroubleshoot (daemon)| `setroubleshootd` |
| Herstellen initiële SELinux-settings| `restorecon -R -v [target-folder]`(bijv. /var/www) |
| Config files selinux | `/etc/selinux/config `                         |
| Labeling controleren (optie -Z) | `ls -lZ [/usr/sbin/httpd]`                       |
| Change context | `chcon` |
| Ingestelde booleans opvragen | `getsebool -a` (en evt. `| grep samba/smbd/nmbd`) |
| Een boolean instellen| `setsebool [boolean] [0|1]` (-P toevoegen om permanent te maken) |
| (na install setroubleshoot) | `sealert -l [de opgegeven code]` |
| Grafische tool| `system-config-selinux` |
| SELinux-Alerts vinden in de logs | `sealert -a /var/log/audit/audit.log | less` |

* ls -Z
* netstat -Z
* 
###Testen ###

Wanneer een script niet runt in combinatie met een Windows-host (door einde-markeringen, eigen aan Microsoft):

`yum install dos2unix -f`.

Run vervolgens `dos2unix` [script].

### Hardware ###
* lspci (al de PCI-bussen en apparaten van het systeem)
* `lsppci -n` (identificatiecodes: laatste kolom cijfers en letters geven _Fabrikant:type apparaat_ weer )
* ~= >> 
    hwinfo

### IP-adressen configureren ###
* In plaats van ifconfig, NU _ip add_ / _ip address_
* IP-adressen manueel aanpassen: vi /etc/sysconfig/network-scripts/ifcfg-eth0
* `ping -c 5` [ip address]

### Firewall en DNS ###
* `lsof -i -n -P | grep` ... ( list open files, geeft lijst geopende bestanden en door welke processen deze gebruikt worden, weer) 
<br>Opties:
      * -i: sockets
      * -n: gebruik geen DNS
      * -P: toon poortnummers
* arp [Adress Resolution Protocol config](http://xmodulo.com/how-to-add-or-remove-static-arp-entry-on-linux.html)
* Firewall: /etc/sysconfig/iptables
    * systemctl restart iptables.service
* Default gateway: 
    * `netstat -rn`
    * `route -n`
* DNS: /etc/resolv.conf
* `nmap -p ftp,http`

### Services controleren ###

* Service is depricated, gebruik in de plaats:
    * _systemctl_ start httpd.service
    * systemctl status httpd.service
    * systemctl enable httpd.service
    * systemctl disable httpd.service
* `top`
* `ps | grep` [naam_service]
* SAMBA: 
    * systemctl status smb.service (daemon)
    * systemctl status nmb.service (daemon)
* FTP: 
    * systemctl status vsftpd.service

* tailof `less` /var/logs/messages
      * (en verdere logs in de directory logs)
      * zoek dan naar DHCP op deze manier: /DHCP


* Vergeet niet de service 'remote' te testen (op je host-machine)
