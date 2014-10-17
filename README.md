EL Cheatsheets and checklists
=============================

Cheat sheets en checklists ivm Enterprise Linux

## Git (Bitbucket & GitHub)

Hoewel je veel met aliases werkt, toch enkele commands voor mocht je een paar aliases vergeten zijn ;-)

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
| Vagrant box herladen (voor niet al te zware wijzigingen  | `vagrant reload (evt. naam host toevoegen)`                       |
| Vagrant box wegdoen en opnieuw opzetten in 1 handeling (wnnr zware wijzigingen  | `vagrant destroy && up (evt. naam host toevoegen)`                       |
| Vagrant ssh'en                | `vagrant ssh (naam VM)` |
| Vagrant status krijgen                | `vagrant status (evt. naam host)` |


