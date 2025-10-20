# Mediaserver Stack

Docker Compose stack for Abel's mediaserver, bundling VPN-protected downloaders, indexers, media managers, and frontends on the shared `media` network.

## Gebruik
1. Pas paden in `docker-compose.yml` aan je eigen host aan (config en mediapaden).
2. Vul de vereiste environment-variabelen in een `.env` bestand of je deployment tooling.
3. Pas in `sabnzbd.ini` (pad: `/mnt/docker/stack-mediaserver/sabnzbd/sabnzbd.ini`) handmatig de `port` waarde aan naar `8081` voordat je SABnzbd start.
4. Start de stack met `docker compose up -d`.

## Environment variabelen
| Naam | Verplicht | Default | Beschrijving |
| --- | --- | --- | --- |
| `PUID` | Nee | `1000` | Linux user ID die de containers moeten gebruiken voor permissies. |
| `PGID` | Nee | `1000` | Linux group ID die de containers moeten gebruiken voor permissies. |
| `WIREGUARD_PRIVATE_KEY` | Ja | – | WireGuard private key voor de gluetun VPN. |
| `WIREGUARD_ADDRESSES` | Nee | `10.13.13.2/32` | Interne WireGuard IP(s) voor gluetun. |
| `WIREGUARD_ENDPOINT_IP` | Nee | – | Custom endpoint IP voor WireGuard (optioneel). |
| `WIREGUARD_ENDPOINT_PORT` | Nee | `51820` | Custom endpoint poort voor WireGuard (optioneel). |
| `WIREGUARD_PUBLIC_KEY` | Nee | – | Public key van de WireGuard server (indien vereist). |
| `WIREGUARD_PRESHARED_KEY` | Nee | – | Pre-shared key voor WireGuard (optioneel). |
| `BRIGHT_PROXY_USERNAME` | Nee | – | Inlognaam voor Bright Data proxy (voor `flaresolverr-brightdata`). |
| `BRIGHT_PROXY_PASSWORD` | Nee | – | Wachtwoord voor Bright Data proxy. |
| `BOOKLORE_DB_ROOT_PASSWORD` | Nee | `change_me_root` | Root-wachtwoord voor de optionele Booklore MariaDB. |
| `BOOKLORE_DB_PASSWORD` | Nee | `change_me` | Applicatie-wachtwoord voor Booklore. |

> De Booklore-variabelen zijn alleen nodig wanneer je de uit-gecommentarieerde Booklore-services activeert.

