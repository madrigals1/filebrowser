# Filebrowser

Dropbox-like file manager, that can be set up on any server. My settings add functionality to use it through HTTPS.

## Demo

![Demo](https://user-images.githubusercontent.com/5447088/50716739-ebd26700-107a-11e9-9817-14230c53efd2.gif)

## Prerequisites

Make sure you have installed these:
- [Docker and Docker Compose](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04) - Will install all the required packages and software.
- (Optional) [Dockerized Nginx with SSL](https://github.com/madrigals1/nginx) - Will generate SSL certificates and make the app accessible through `SSL_DOMAIN`, that is set inside `.env`.

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
- SSL settings (Not needed without **Dockerized Nginx**):
    - `SSL_DOMAIN` - domain of the website with VizAPI
    - `HTTPS_NETWORK` - network, in which our HTTPS server will be running. 

```dotenv
# Docker settings
UID=0
GID=0
HTTPS_NETWORK=https_network
DOCKER_STATIC_HOSTING=/var/www/static

# Lets encrypt settings
SSL_DOMAIN=filebrowser.example.com
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

- Access **Filebrowser** instance through `SSL_DOMAIN` or `localhost:PORT` from browser.
- Initial credentials are **login: admin** and **password: admin**

## Authors
- Adi Sabyrbayev [Github](https://github.com/madrigals1), [LinkedIn](https://www.linkedin.com/in/madrigals1/)
