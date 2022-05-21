
# Deluge integrated with Plex

Docker with Deluge BitTorrent Client and Stream Movies & TV Shows | Plex




## Functionalities

- Media download that can be streamed in real time upon completion in the Plex catalog.
- Easy administration by using volume mapping application configuration is saved on volumes.
- Shared volume in Docker configuration between Deluge and Plex
- Both sharing the same volume, so Deluge complete is now available for Plex.


## Reference

 - [LinuxServer.io | Plex](https://hub.docker.com/r/linuxserver/plex)
 - [LinuxServer.io | Deluge](https://hub.docker.com/r/linuxserver/deluge)
 - [LinuxServer.io | Forum](https://discourse.linuxserver.io/)


## Application Setup - Deluge

The admin interface is available at http://SERVER-IP:8112 with a default user/password of admin/deluge.

To change the password (recommended) log in to the web interface and go to Preferences->Interface->Password.

Change the inbound port to 6881 (or whichever port you've mapped for the container) under Preferences->Network, otherwise random ports will be used.

Attention to the Volume that will map in the container point the same to the Plex container in the case I used the one below:

Deluge
```bash
    volumes:
      - /path/to/deluge/config:/config
      - /path/to/your/downloads:/downloads
```
Plex
```bash
    volumes:
      - /path/to/library:/config
      - /path/to/your/downloads:/tv
      - /path/to/movies:/movies
```


## Application Setup - Plex

Webui can be found at <your-ip>:32400/web

** Note about updates, if there is no value set for the VERSION variable, then no updates will take place.**

** For new users, no updates will take place on the first run of the container as there is no preferences file to read your token from, to update restart the Docker container after logging in through the webui**

Valid settings for VERSION are:-

IMPORTANT NOTE:- YOU CANNOT UPDATE TO A PLEXPASS ONLY (BETA) VERSION IF YOU ARE NOT LOGGED IN WITH A PLEXPASS ACCOUNT

docker: Let Docker handle the Plex Version, we keep our Dockerhub Endpoint up to date with the latest public builds. This is the same as leaving this setting out of your create command.
latest: will update plex to the latest version available that you are entitled to.
public: will update plexpass users to the latest public version, useful for plexpass users that don't want to be on the bleeding edge but still want the latest public updates.
<specific-version>: will select a specific version (eg 0.9.12.4.1192-9a47d21) of plex to install, note you cannot use this to access plexpass versions if you do not have plexpass.
## Environment variables

These environment variables came empty because they are optional.

Deluge
`DELUGE_LOGLEVEL=error #optional`

Plex
`PLEX_CLAIM= #optional`


## Running Locally

Clone the Project

```bash
  git clone https://github.com/omztg/deluge-plex/blob/main/docker-compose.yml
```
Start the server

```bash
  docker-compose up -d
```


## Hardware used

**Virtual Machine:**  Memory usage 2.00 GiB, 4 CPU(s), Hard Disk 720G

**Operational system:** Debian GNU/Linux 11 (bullseye) Node proxmox

**Docker version:** 20.10.5+dfsg1, build 55c4c88

## 🚀 About me
Infrastructure Analyst | DevOps student


## 🔗 Links
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tiago-menegon-zimmermann-97a67b1b6/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/omz_tg)


## 🛠 Skills
Linux, Shell Script, Docker, Kubernetes, Ansible, Jenkins, Terraform, Python

