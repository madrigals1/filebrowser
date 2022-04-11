# Filebrowser

Dropbox-like file manager, that can be set up on any server. My settings add functionality to use it through HTTPS.

## Demo

![Demo](https://user-images.githubusercontent.com/5447088/50716739-ebd26700-107a-11e9-9817-14230c53efd2.gif)

## Prerequisites

Make sure you have installed these:
- [Docker and Docker Compose](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04) - Will install all the required packages and software.
- (Optional) [Dockerized Nginx](https://github.com/madrigals1/nginx_proxy_manager) - Will generate SSL certificates and make the app accessible through `HTTPS_NETWORK`, that is set inside `.env`.

## Installation

Make a copy of `.env.example` file named `.env`

```shell script
cp .env.example .env
```

---

Environment variables:
- `UID` and `GID` - user and group, whose access will be used for this **Filebrowser** instance.
- `PORT` - port on which the app will be running.
- `DOCKER_STATIC_HOSTING` - folder, that will be displayed.
- HTTPS settings (Not needed without **Dockerized Nginx**):
    - `HTTPS_NETWORK` - network, in which our **Dockertized Nginx** is running. 

```dotenv
# Docker settings
UID=0
GID=0
HTTPS_NETWORK=https_network
DOCKER_STATIC_HOSTING=/var/www/static
PORT=8888
```

---

Create network with the name, that we have in `HTTPS_NETWORK` environment variable.

```shell script
docker network create https_network
```

---

Build the Docker image

```shell script
docker-compose build
```

## Running

Start
```
docker-compose up
```

Stop
```
docker-compose down
```

## Usage

- Access **Filebrowser** instance `localhost:${PORT}` from browser or create Certificate and Proxy Host using [Dockerized Nginx](https://github.com/madrigals1/nginx_proxy_manager) .

## Authors
- Adi Sabyrbayev [Github](https://github.com/madrigals1), [LinkedIn](https://www.linkedin.com/in/madrigals1/)
