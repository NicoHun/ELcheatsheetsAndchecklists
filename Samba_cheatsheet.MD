EL Cheatsheets and checklists
=============================

_Nico Hunink (3 TIN HoGent)_ 

### Samba_cheatsheet

### Tools
* `yum install setroubleshoot`, gevolgd door: `restart auditd`
* `journalctl`
* `repoquery -qf */netstat */lsof */nmap`
      * Wanneer niet geïnstalleerd: `yum install yum-utils`
* `yum install net-tools`
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
| In de logs controleren op output van setroubleshoot | `grep setroubleshoot /var/log/messages` |
| Config files SELinux | `/etc/selinux/config `                         |
| Labeling controleren (optie -Z) | `ls -lZ [/usr/sbin/httpd]`                       |
| Change context | `chcon` |
| Ingestelde booleans opvragen | `getsebool -a` (en evt. `| grep samba/smbd/nmbd`) |
| Een boolean instellen| `setsebool [boolean] [0|1]` (-P toevoegen om permanent te maken) |
| (na install setroubleshoot) | `sudo sealert -l [de opgegeven code]` |
| Grafische tool| `sudo system-config-selinux` |
| SELinux-Alerts vinden in de logs | `sudo sealert -a /var/log/audit/audit.log | less` |

* ls -Z
* netstat -Z

###Testen ###

Wanneer een script niet runt in combinatie met een Windows-host (door einde-markeringen, eigen aan Microsoft):

`yum install dos2unix -f`.

Run vervolgens `dos2unix` [script].

### IP-adressen configureren ###
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
* DNS: /etc/resolv.conf
* `nmap -p ftp,http`

### Services controleren ###

* Service is depricated, gebruik in de plaats:
    * _systemctl_ start httpd.service
* SAMBA: 
    * systemctl status smb.service (daemon)
    * systemctl status nmb.service (daemon)
* FTP: 
    * systemctl status vsftpd.service
* `top`
* `ps | grep` [naam_service]
* `tail -f less /var/logs/messages`
      * (en verdere logs in de directory logs)
      * zoek dan naar DHCP op deze manier: /DHCP

