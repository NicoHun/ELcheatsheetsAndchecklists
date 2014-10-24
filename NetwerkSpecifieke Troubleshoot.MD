
## Fysical/data link layer
1. Kabels ingeplugd?
        - Kabel niet kapot? (branden de lichtjes, aan beide kanten?)
2. Netwerk laag: lokale config
      - `ip add`
        - def gateway? ip route
3. DNS : cat /etc/resolv.conf
4. Network laag: remote config
        - Ping de def gateway (*)
        - DNS servers: dig www.example.com @x.y.z.w

(*) Ping werkt niet altijd. Gebruik dus traceroute (```tracert```) in de plaats.

## Network services: bijv. httpd

Je hebt service gestart, maar deze geeft niet thuis.

Valideer network config van de server!

1. Validate configuration file
    - `apachectl configtest`
2. Controleer of de service draait:
    - `sudo netstat -tlnp` (options: `t` = tcp, `l` = listening, `n` = poortnummers, `p` = proces)
    - `sudo systemctl *status* httpd.service`
3. Log-bestanden controleren op fouten: `journalctl -b -u httpd`
4. Test lokaal (surfen naar bijv. 127.0.0.1:80(80)):
    - `*wget* http://localhost:8080`
    - `*curl* http://localhost:8080` !!
5. Test remote:
    - bijv. browser (op host machine)
    - `sudo nmap -sS -p 80` (perform a TCP SYN scan on port 80 using `nmap`)
6. Check firewall settings
    - `sudo iptables -L -n -v`
    - `firewalld` oF `/etc/sysconfig/iptables` (vergeet niet te restarten na aanpassen firewallregels)
