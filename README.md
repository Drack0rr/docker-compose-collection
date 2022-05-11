
# Docker-compose by PAPAMICA
|  ![PAPAMICA](https://zupimages.net/up/20/04/7vtd.png) |  [Wiki-Tech.io](https://Wiki-Tech.io/)<br/> [Tech2Tech.fr](https://www.tech2tech.fr/) <br/> [Twitter @PAPAMICA__](https://twitter.com/PAPAMICA__) <br/> [LinkedIn](https://www.linkedin.com/in/mickael-asseline/)<br/> |
|:--------:| :-------------|


These docker-compose allow you to deploy multiple services easily and quickly. You can use them with Portainer directly or via docker-compose commands.
All docker-compose are commented and are configured using variables.

They all include support for Traefik.

You can deploye a compatible Docker environment with Portainer and Traefik with :
https://github.com/PAPAMICA/docker-environment



## List of services availables:
| Status | Service | Update |
|:--:|--|--|
| ✅ | adminer.yml | 10/05/2022
 |
| ✅ | bookstack.yml | 10/05/2022
 |
| ✅ | cachethq.yml | 10/05/2022
 |
| ✅ | etherpad.yml | 10/05/2022
 |
| ✅ | filebot.yml | 10/05/2022
 |
| ✅ | filebrowser.yml | 10/05/2022
 |
| 🚸 | gitlab.yml | 10/05/2022
 |
| ✅ | grafana.yml | 10/05/2022
 |
| ✅ | hastebin.yml | 10/05/2022
 |
| ✅ | jirafeau.yml | 10/05/2022
 |
| ✅ | keycloak.yml | 10/05/2022
 |
| ✅ | matomo.yml | 10/05/2022
 |
| 🚸 | nextcloud.yml | 10/05/2022
 |
| 🚸 | openvpn.yml | 10/05/2022
 |
| 🚸 | ouroboros.yml | 10/05/2022
 |
| 🚸 | privatebin.yml | 10/05/2022
 |
| 🚸 | projectsend.yml | 10/05/2022
 |
| 🚸 | shorturl.yml | 10/05/2022
 |
| 🚸 | sinusbot.yml | 10/05/2022
 |
| 🚸 | taiga.yml | 10/05/2022
 |
| 🚸 | teamspeak.yml | 10/05/2022
 |
| 🚸 | traefik.yml | 10/05/2022
 |
| 🚸 | ts3rank.yml | 10/05/2022
 |
| 🚸 | ts3viewer.yml | 10/05/2022
 |
| ✅ | umami.yml | 10/05/2022
 |
| 🚸 | vault.yml | 10/05/2022
 |
| ✅ | vaultwarden.yml | 10/05/2022
 |
| 🚸 | vscode.yml | 10/05/2022
 |
| ✅ | website-html.yml | 10/05/2022
 |
| 🚸 | wikijs.yml | 10/05/2022
 |
| 🚸 | wiznote.yml | 10/05/2022
 |
| 🚸 | wordpress.yml | 10/05/2022
 |
| 🚸 | yourls.yml | 10/05/2022
 |
| 🚸 | zabbix-cachethq.yml | 10/05/2022
 |
| 🚸 | zabbix-proxy.yml | 10/05/2022
 |
| 🚸 | zabbix.yml | 10/05/2022
 |


# Utilisation
## Portainer
Add the URL of my repo directly in Portainer:
![PORTAINER](https://i.imgur.com/M49ssCN.png)

## Debian
Install Git :
```bash
 apt install -y git
```

Clone repo
```bash
git clone https://github.com/PAPAMICA/docker-compose-collection/
```


Configuration of variables and execution of a docker-compose:
```bash
cd docker-compose-collection
nano env
sudo docker-compose -f service.yml --env-file env up -d
```
## Some useful commands:

-   **docker container ls** : Show current Docker containers
-   **docker-compose stop** : Stop the containers created with the scripts (in the script folder)
- **docker-compose up -d** : Launch the containers created with the scripts (in the script folder)
-   **docker logs -f <id_container>** : Display the container logs
-   **docker exec -it <id_container> bash** : Get a shell in container
