
# Docker-compose by PAPAMICA

<p align="center">
  <a href="https://papamica.com">
    <img src="https://zupimages.net/up/20/04/7vtd.png" width="140px" alt="PAPAMICA" />
  </a>
</p>
<p align="center">
    <a href="https://github.com/PAPAMICA/docker-compose-collection#list-of-services-availables">List of services</a> |
    <a href="https://github.com/PAPAMICA/docker-compose-collection#utilisation">How to use</a> |
    <a href="https://github.com/PAPAMICA/docker-compose-collection#add-new-docker-compose-file">Add a new service</a>
    <br /><br />
</p>


These docker-compose allow you to deploy multiple services easily and quickly. You can use them with Portainer directly or via docker-compose commands.
All docker-compose are commented and are configured using variables.

They all include support for Traefik.

You can deploye a compatible Docker environment with Portainer and Traefik with:

https://github.com/PAPAMICA/docker-environment



## List of services availables:
| Status | Service | Update |
|:--:|--|--|
| ✅ | adminer.yml | 2022-10-05 |
| ✅ | bookstack.yml | 2022-10-05 |
| ✅ | cachethq.yml | 2022-10-05 |
| ✅ | etherpad.yml | 2022-10-05 |
| ✅ | filebot.yml | 2022-10-05 |
| ✅ | filebrowser.yml | 2022-10-05 |
| 🚸 | gitlab.yml | - |
| ✅ | grafana.yml | 2022-10-05 |
| ✅ | hastebin.yml | 2022-10-05 |
| ✅ | jirafeau.yml | 2022-10-05 |
| ✅ | keycloak.yml | 2022-10-05 |
| ✅ | matomo.yml | 2022-10-05 |
| 🚸 | nextcloud.yml | - |
| 🚸 | openvpn.yml | - |
| 🚸 | ouroboros.yml | - |
| 🚸 | privatebin.yml | - |
| 🚸 | projectsend.yml | - |
| 🚸 | shorturl.yml | - |
| 🚸 | sinusbot.yml | - |
| 🚸 | taiga.yml | - |
| 🚸 | teamspeak.yml | - |
| 🚸 | traefik.yml | - |
| 🚸 | ts3rank.yml | - |
| 🚸 | ts3viewer.yml | - |
| ✅ | umami.yml | 2022-05-10 |
| 🚸 | vault.yml | - |
| ✅ | vaultwarden.yml | 2022-05-10 |
| ✅ | vscode.yml | 2022-05-11 |
| ✅ | website-html.yml | 2022-05-10 |
| 🚸 | wikijs.yml | - |
| 🚸 | wiznote.yml | - |
| 🚸 | wordpress.yml | - |
| 🚸 | yourls.yml | - |
| 🚸 | zabbix-cachethq.yml | - |
| 🚸 | zabbix-proxy.yml | - |
| 🚸 | zabbix.yml | - |

---
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

---
# Add new docker-compose file
I automated the creation of the json template file for Portainer and the update of the README.md.

If you want to add a new docker-compose, you must use the following template:
```yaml
# Docker-compose provided by Mickael "PAPAMICA" Asseline
# Update: 2022-10-05

#& type: 3
#& title: Hastebin
#& description: Share your code easily
#& note: Website: <a href='https://hastebin.com/about.md' target='_blank' rel='noopener'>Hastebin.com</a>
#& categories: SelfHosted, PAPAMICA
#& platform: linux
#& logo: https://progsoft.net/images/hastebin-icon-b45e3f5695d3f577b2630648bd00584195822e3d.png

#% SERVICE: Name of the service (No spaces or points)
#% DATA_LOCATION: Data localization (Example: /apps/service)
#% URL: Service URL (Example: service.papamica.fr or service.com)
#% NETWORK: Your Traefik network (Example: proxy)

# Work with Portainer
version: "2"
services:
  # Hastebin : https://hastebin.com/about.md
  hastebin:
    image: rlister/hastebin:latest
    container_name: $SERVICE
    restart: always
    environment:
      STORAGE_TYPE: file
    volumes:
      - $DATA_LOCATION/data:/data
    healthcheck:
      test: wget -s 'http://localhost:7777'
      interval: 1m
      timeout: 30s
      retries: 3 
    networks:
      - default
    labels:
      - "autoupdate=monitor" # https://github.com/PAPAMICA/container-updater
      - "traefik.enable=true"
      - "traefik.http.routers.$SERVICE.entrypoints=https"
      - "traefik.http.routers.$SERVICE.rule=Host(`$URL`)"
      - "traefik.http.routers.$SERVICE.tls=true"
      - "traefik.http.routers.$SERVICE.tls.certresolver=http"
      - "traefik.docker.network=$NETWORK"
      
networks:
  default:
    external:
      name: $NETWORK
```