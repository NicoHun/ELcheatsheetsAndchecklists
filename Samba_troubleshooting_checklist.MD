EL Cheatsheets and checklists - Nico Hunink (3 TIN HoGent)
=============================

# Samba_troubleshooting_checklist #

1) Services controleren

* SAMBA: 
    * systemctl status smb.service (daemon)
    * systemctl status nmb.service (daemon)
* FTP: 
    * systemctl status vsftpd.service
    
2) Samba config-file controleren
`testparm smb.conf`

3) Check DNS: is deze actief en werkt deze correct?
`cat /etc/resolv.conf`

4) Firewall controleren
`iptables -L -v`

5) Shares controleren
`smbclient -L [naam server]`

6) Zoek het IP-adres van de Samba-server
nmblookup -B [naamServer] __SAMBA__

Wanneer niet weergegeven, Controleer `inetd.conf`-file

7) Zoek het IP-adres van de master browser van de werkgroep
nmblookup -M [naamWerkgroep]

