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
mkdir -p "$HOME/.local/share/srv/docker/postfix/rootfs"
git clone "https://github.com/dockermgr/postfix" "$HOME/.local/share/CasjaysDev/dockermgr/postfix"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/." "$HOME/.local/share/srv/docker/postfix/rootfs/"
docker run -d \
  --name casjaysdevdocker-postfix-latest \
  --hostname $HOSTNAME \
  -e "HOSTNAME=$HOSTNAME" \
  -e "DOMAINS=example.com,example2.com" \
  -v "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/data:/data" \
  -v "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/config:/config" \
  -p 25:25 \
  casjaysdevdocker/postfix:latest
```
  
## via docker-compose  
  
```yaml
version: '3.9'
services:
    postfix:
        privileged: true
        hostname: $HOSTNAME
        image: 'casjaysdevdocker/postfix:latest'
        container_name: casjaysdevdocker-postfix-latest
        ports:
            - '25:25'
        volumes:
            - "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/data:/data"
            - "$HOME/.local/share/CasjaysDev/dockermgr/postfix/rootfs/config:/config"
        environment:
            - "HOSTNAME=$HOSTNAME"
            - "DOMAINS=example.com,example2.com"
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
