# My Custom Umbrel App Store

A comprehensive community app store for [UmbrelOS](https://umbrel.com) with **45+ self-hosted Docker apps** across 7 categories.

## How to add this store to Umbrel

1. Open your Umbrel dashboard
2. Navigate to **App Store** → **Community App Stores**
3. Click **Add Store**
4. Enter the URL of this GitHub repository:
   ```
   https://github.com/YOUR_USERNAME/umbrel-app-store
   ```
5. Click **Add** – the store will appear in your App Store immediately!

> **Note:** Replace `YOUR_USERNAME` with your actual GitHub username after pushing this repo.

---

## App Overview (45 Apps)

### 🗂️ Productivity (10 Apps)

| App | Description | Port |
|-----|-------------|------|
| **Nextcloud** | Self-hosted file sync, cloud storage & collaboration | 8080 |
| **Vaultwarden** | Bitwarden-compatible password manager | 3012 |
| **Paperless-ngx** | Document management with OCR (supports German!) | 8000 |
| **BookStack** | Self-hosted wiki and documentation platform | 6875 |
| **Joplin Server** | Sync server for the Joplin note-taking app | 22300 |
| **Outline** | Fast, collaborative knowledge base & team wiki | 3003 |
| **Vikunja** | To-do app with Kanban, Gantt, calendar views | 3456 |
| **Mealie** | Recipe manager and meal planner with web import | 9925 |
| **Linkding** | Minimal self-hosted bookmark manager | 9090 |
| **Wallabag** | Read-it-later app, save articles for offline reading | 8095 |

---

### 📊 Monitoring (7 Apps)

| App | Description | Port |
|-----|-------------|------|
| **Grafana** | Metrics dashboards and observability platform | 3001 |
| **Uptime Kuma** | Self-hosted uptime and status page monitoring | 3002 |
| **Netdata** | Real-time system performance monitoring | 19999 |
| **Prometheus** | Metrics collection and time series database | 9091 |
| **Homarr** | Modern homelab dashboard with Docker integration | 7575 |
| **Homer** | Lightweight static server homepage | 8888 |
| **Glances** | Cross-platform system overview with web UI | 61208 |

---

### 🌐 Netzwerk & Security (7 Apps)

| App | Description | Port |
|-----|-------------|------|
| **Pi-hole** | Network-wide ad blocker via DNS | 8053 |
| **AdGuard Home** | DNS-based ad & tracker blocker | 3000 |
| **WireGuard Easy** | WireGuard VPN with simple web management | 51821 |
| **Nginx Proxy Manager** | Easy reverse proxy with Let's Encrypt SSL | 81 |
| **Traefik** | Cloud-native reverse proxy with auto-HTTPS | 8880 |
| **Cloudflare Tunnel** | Expose services without opening firewall ports | — |
| **Tailscale** | Zero-config WireGuard-based VPN mesh | — |

---

### 💰 Finanzen (5 Apps)

| App | Description | Port |
|-----|-------------|------|
| **Firefly III** | Full-featured personal finance manager (double-entry) | 8040 |
| **Actual Budget** | Fast, local-first envelope budgeting app | 5006 |
| **Grocy** | Household & grocery management with finance tracking | 9283 |
| **Ghostfolio** | Portfolio & wealth tracker for stocks, ETFs, crypto | 3333 |
| **Maybe Finance** | Open-source personal finance OS | 3444 |

---

### 🔐 IT-Security (6 Apps)

| App | Description | Port |
|-----|-------------|------|
| **CyberChef** | Web app for encryption, encoding & data analysis | 8765 |
| **CrowdSec** | Open-source collaborative intrusion prevention | 8080 |
| **Authentik** | Self-hosted SSO / Identity Provider (OAuth2, SAML) | 9000 |
| **Wazuh** | Open-source XDR & SIEM security platform | 443 |
| **IT Tools** | Collection of handy online tools for IT professionals | 8111 |
| **Portainer** | Docker & container management web UI | 9444 |

---

### 👤 Personal Management (5 Apps)

| App | Description | Port |
|-----|-------------|------|
| **Monica** | Personal CRM – organize your social life & contacts | 8200 |
| **Immich** | High-performance self-hosted photo & video backup | 2283 |
| **PhotoPrism** | AI-powered photo management with face recognition | 2342 |
| **Kavita** | Fast reading server for manga, comics & eBooks | 5000 |
| **Calibre Web** | Web interface for your Calibre eBook library | 8083 |

---

### 🚗 Car & Vehicle (5 Apps)

| App | Description | Port |
|-----|-------------|------|
| **TeslaMate** | Self-hosted data logger & Grafana dashboards for Tesla | 4000 |
| **EVCC** | EV charging manager with solar surplus optimization | 7070 |
| **Traccar** | Open source GPS tracking platform (170+ protocols) | 8082 |
| **OpenWB 2** | German open-source EV wall box control software | 8500 |
| **Node-RED** | Flow-based automation for vehicle APIs & IoT | 1880 |

---

## Configuration Notes

### WireGuard Easy
Edit `docker-compose.yml` and replace `YOUR_SERVER_IP` with your public IP address.

### Cloudflare Tunnel
1. Create a tunnel in the [Cloudflare Zero Trust dashboard](https://dash.cloudflare.com)
2. Copy your tunnel token
3. Edit `docker-compose.yml` and replace `YOUR_TUNNEL_TOKEN_HERE`

### Tailscale
1. Generate an auth key at [tailscale.com/admin/settings/keys](https://login.tailscale.com/admin/settings/keys)
2. Replace `YOUR_TAILSCALE_AUTHKEY` in `docker-compose.yml`

### EVCC
EVCC requires a configuration file. Mount your `evcc.yaml` at `/etc/evcc.yaml`.
Use the [EVCC documentation](https://docs.evcc.io) to configure your charger, vehicle and meter.

### TeslaMate
After starting, visit the UI and log in with your Tesla account credentials. TeslaMate will start pulling data immediately.

### Authentik
After first start, visit `http://YOUR-IP:9000/if/flow/initial-setup/` to set the admin password.

---

## Directory Structure

```
umbrel-app-store/
├── umbrel-app-store.yml          # Store definition
├── my-store-nextcloud/
│   ├── umbrel-app.yml            # App metadata
│   └── docker-compose.yml        # Docker services
├── my-store-vaultwarden/
│   ├── umbrel-app.yml
│   └── docker-compose.yml
... (one directory per app)
```

---

## Security Reminder

All default passwords in this store are **placeholders**. Before running any app in production, change:
- All database passwords
- `APP_KEY` / `SECRET_KEY` / `JWT_SECRET` values
- Admin credentials
- Encryption keys

---

## Contributing

Pull requests welcome! To add a new app, create a directory `my-store-<appname>/` with:
- `umbrel-app.yml` (app metadata following the [Umbrel app manifest spec](https://github.com/getumbrel/umbrel-apps))
- `docker-compose.yml` (Docker Compose v3.7 services)

---

## License

MIT License – see [LICENSE](LICENSE)
