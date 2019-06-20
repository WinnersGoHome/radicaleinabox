# radicaleinabox

A containerized [radicale](https://github.com/Kozea/Radicale) server.

## Setup
Make sure Docker and docker-compose are installed.

    git clone https://github.com/WinnersGoHome/radicaleinabox.git && cd radicaleinabox/
    docker-compose up

## Add Users
Run an ubuntu container and mount the volumes from the radicaleinabox uwsgi:

    docker run -it --volumes-from radicaleinabox_uwsgi_1 ubuntu:latest /bin/bash

Inside the ubuntu container:

    apt update && apt install apache2-utils
    htpasswd -B /usr/local/radicale/data/users <username>
