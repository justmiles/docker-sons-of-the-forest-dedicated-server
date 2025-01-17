## Docker - Sons of the Forest Dedicated Server

This includes a Sons of the Forest Dedicated Server based on Docker with Wine and an example config.

## What you need to run this

- Basic understanding of Linux and Docker

## Getting started

1. Create 2 sub-directories on your Dockernode in your game-server-directory (`/srv/sonsoftheforest/steamcmd` and `/srv/sonsoftheforest/game`)
2. Start the container with the following examples:

Bash:

```console
docker run --rm -i -t -p 8766:8766/udp -p 27016:27016/udp -p 9700:9700/udp -v $(pwd)/steamcmd:/steamcmd -v $(pwd)/game:/sonsoftheforest --name sons-of-the-forest-dedicated-server jammsen/sons-of-the-forest-dedicated-server:latest
```

Docker-Compose:

```yaml
version: '3.9'
services:
  sons-of-the-forest-dedicated-server:
    container_name: sons-of-the-forest-dedicated-server
    image: jammsen/sons-of-the-forest-dedicated-server:latest
    restart: always
    environment:
      ALWAYS_UPDATE_ON_START: 1
    ports:
      - 8766:8766/udp
      - 27016:27016/udp
      - 9700:9700/udp
    volumes:
      - ./steamcmd:/steamcmd
      - ./game:/sonsoftheforest
      - ./winedata:/winedata
```

## Planned features in the future

Nothing yet

## Software used

- Debian Slim Stable
- Xvfb
- Winbind
- Wine
- SteamCMD
- SonsOfTheForest Dedicated Server
