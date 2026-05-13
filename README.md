## 👋 Welcome to postfix 🚀  

postfix README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update postfix
```
  
## Install and run container
  
```shell
dockerHome="/var/lib/srv/$USER/docker/casjaysdevdocker/postfix/postfix/latest/rootfs"
mkdir -p "/var/lib/srv/$USER/docker/postfix/rootfs"
git clone "https://github.com/dockermgr/postfix" "$HOME/.local/share/CasjaysDev/dockermgr/postfix"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/." "$dockerHome/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-postfix-latest \
--hostname postfix \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$dockerHome/data:/data:z" \
-v "$dockerHome/config:/config:z" \
-p 80:80 \
casjaysdevdocker/postfix:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/postfix
    container_name: casjaysdevdocker-postfix
    environment:
      - TZ=America/New_York
      - HOSTNAME=postfix
    volumes:
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/postfix/postfix/latest/rootfs/data:/data:z"
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/postfix/postfix/latest/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/postfix
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/postfix" "$HOME/Projects/github/casjaysdevdocker/postfix"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/postfix"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
