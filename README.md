# proxy-api

Lightweight Express service that aggregates free proxy lists, health-checks them, and serves live results as JSON.

## Features

- Sources HTTP / HTTPS / SOCKS4 / SOCKS5 lists from configurable providers (`proxy.json`)
- Live check against a target site (`config.json` → `site`)
- Optional GeoIP enrichment via [ipinfo.io](https://ipinfo.io)
- Periodic refresh (`fetch_interval`, default 900s)
- Simple REST query API

## Stack

- Node.js · Express · Axios · Moment

## Quick start

```bash
git clone https://github.com/duckzangryy/proxy-api.git
cd ProxyAPI
npm install express axios moment json-beautify   # or npm i if package.json is added
node index.js
```

Server listens on **port 80** by default (needs root / capability, or change `port` in `index.js`).

## Configuration

### `config.json`

| Key | Meaning |
|-----|---------|
| `site` | URL used for live proxy checks |
| `timeout` | Request timeout (seconds) |
| `fetch_interval` | Seconds between list refreshes |
| `max_ms` | Max acceptable latency |
| `check_google` | Extra reachability flag |

### `proxy.json`

Lists of provider URLs per protocol (`https`, `http`, `socks5`, `socks4`). Providers may return plain `ip:port` text or JSON.

## API

| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/api/proxy?type=all&format=json` | All live proxies |
| `GET` | `/api/proxy?type=https&format=json` | HTTPS only |
| `GET` | `/api/proxy?type=http&format=json` | HTTP only |
| `GET` | `/api/proxy?type=socks5&format=json` | SOCKS5 only |
| `GET` | `/api/proxy?type=socks4&format=json` | SOCKS4 only |

### Example response

```json
{
  "status": 200,
  "total": 42,
  "last_check": "2026-07-18 09:00:00",
  "proxies": ["203.0.113.10:8080", "198.51.100.5:3128"]
}
```

## Notes

- Free public proxies are unstable; treat this as a **lab / scraper utility**, not production egress.
- Respect provider ToS and local law when using proxies.
- First refresh may take a while while health-checks run.

## License

MIT · [duckzangryy](https://github.com/duckzangryy)
