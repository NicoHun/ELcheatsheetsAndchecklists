EL Cheatsheets and checklists
=============================

_Nico Hunink (3 TIN HoGent)_ 

### Samba_troubleshooting_checklist

1) Services controleren

* SAMBA: 
    * systemctl status smb.service (daemon)
    * systemctl status nmb.service (daemon)
* FTP: 
    * systemctl status vsftpd.service

2) Logs controleren

*	journalctl -r -o verbose -u smb.service 
*	journalctl -r -o verbose -u nmb.service 

3) Samba config-file controleren

`testparm smb.conf`

4) Check DNS: is deze actief en werkt deze correct?

`cat /etc/resolv.conf`

5) SELinux-instellingen controleren

Zie cheatsheet en
- `ausearch -m avc -ts recent -i`
- `grep setroubleshoot /var/log/messages`

6) Firewall controleren

`iptables -L -v`

7) Shares controleren

`smbclient -L [naam server]`

8) Zoek het IP-adres van de Samba-server

`nmblookup -B [naamServer] __SAMBA__`

Wanneer niet weergegeven, Controleer `inetd.conf`-file

9) Zoek het IP-adres van de master browser van de werkgroep
`nmblookup -M [naamWerkgroep]`
