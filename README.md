# Gluetun + qBittorrent (NordVPN) with Docker Compose

This project provides a ready-to-use Docker Compose setup to run **qBittorrent** behind a secure **Gluetun VPN container**.  
It ensures that all qBittorrent traffic is routed through NordVPN (or another provider supported by Gluetun).

---

## Features included in this setup
- ✅ **VPN protection** — all qBittorrent traffic goes through Gluetun’s VPN tunnel (NordVPN by default).  
- ✅ **No leaks** — qBittorrent cannot access the internet unless the VPN is active.  
- ✅ **WebUI access** — qBittorrent WebUI exposed on a configurable host port (`30024` by default).  
- ✅ **Torrenting ports** — TCP/UDP ports (`6881`) mapped for proper torrent connectivity.  
- ✅ **Custom LAN access** — optional LAN subnet allowed via `FIREWALL_VPN_INPUT_ALLOW`.  
- ✅ **Environment-based config** — credentials and settings are stored in a `.env` file, keeping sensitive data out of the compose file.  
- ✅ **Automatic restart** — containers restart automatically unless stopped manually.  
- ✅ **Logging control** — logs limited in size and rotated automatically.  
- ✅ **User/Group IDs** — run qBittorrent with specific `PUID`/`PGID` to match your system permissions.  
- ✅ **Time zone support** — configure container timezone via `TZ`.  

---

## How it works
- **Gluetun** connects to NordVPN and establishes a secure tunnel.  
- **qBittorrent** shares Gluetun’s network stack (`network_mode: service:gluetun`), so all its traffic is forced through the VPN.  
- Only the ports you configure (WebUI and torrenting) are exposed to your host network.  

---

## Files included
- `docker-compose.yml` — defines the Gluetun + qBittorrent containers.  
- `.env.example` — template for environment variables (copy to `.env` and fill with your VPN login).  
- `.gitignore` — prevents committing your real `.env` and local runtime data.  

---

## Quick start

Step 1: Copy the example environment file  
```
cp .env.example .env
```

Step 2: Edit `.env` and add your NordVPN username and password  

Step 3: Start the stack  
```
docker compose up -d
```

Step 4: Check logs  
```
docker compose logs -f gluetun
```

Step 5: Open qBittorrent WebUI at  
```
http://<YOUR-HOST-IP>:30024
```

---

## Security notes
- Never commit your real `.env` file with credentials to GitHub.  
- If you leak credentials, change them immediately.  
- Update `LAN_CIDR` in `.env` if you want LAN access.  

---

## License
MIT — free to use and share.
