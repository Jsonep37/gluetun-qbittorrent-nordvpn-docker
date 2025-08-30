# gluetun-qbittorrent-nordvpn-docker

Docker Compose setup to run qBittorrent routed through Gluetun (NordVPN).  
This repository contains a non-sensitive, example `docker-compose.yml` and `.env.example` so you can run the stack without leaking credentials.

## What this repo provides
- `docker-compose.yml` — gluetun + qBittorrent (qbittorrent uses `network_mode: service:gluetun`)
- `.env.example` — copy to `.env` and populate your VPN credentials locally
- basic `.gitignore` to avoid committing runtime data or secrets

## Prerequisites
- Docker & Docker Compose (or Docker Engine that supports Compose v2)
- A NordVPN account (or other provider supported by gluetun)
- Basic familiarity running commands on the host where you will run containers

## Quick start (safe workflow)
1. Clone your repo locally (or use GitHub web UI to add files).
2. On the host where you will run the stack:
   ```bash
   # create a local .env from the example and edit it
   cp .env.example .env
   # edit .env: set OPENVPN_USER and OPENVPN_PASSWORD and any ports you prefer
