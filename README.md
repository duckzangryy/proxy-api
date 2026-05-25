# ProxyAPI - Horikita Proxy Service

A powerful and lightweight proxy API service that provides access to multiple proxy types including HTTP, HTTPS, SOCKS4, and SOCKS5 proxies. Built for reliability and ease of integration.

## 🚀 Features

- **Multiple Proxy Types** - Supports HTTP, HTTPS, SOCKS4, and SOCKS5 proxies
- **JSON Response Format** - Easy integration with any application
- **Real-time Status** - Monitor proxy availability and count
- **Last Check Timestamp** - Track when proxies were last validated
- **Simple REST API** - Clean and intuitive endpoints

## 📦 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/proxy?type=all&format=json` | GET | Get all available proxies |
| `/api/proxy?type=https&format=json` | GET | Get HTTPS proxies only |
| `/api/proxy?type=http&format=json` | GET | Get HTTP proxies only |
| `/api/proxy?type=socks5&format=json` | GET | Get SOCKS5 proxies only |
| `/api/proxy?type=socks4&format=json` | GET | Get SOCKS4 proxies only |

## 📊 API Response Status

| Service | Path | Status |
|---------|------|--------|
| Horikita All Proxy | `/api/proxy?type=all&format=json` | ✅ 200 OK |
| Horikita HTTPS Proxy | `/api/proxy?type=https&format=json` | ✅ 200 OK |
| Horikita HTTP Proxy | `/api/proxy?type=http&format=json` | ✅ 200 OK |
| Horikita SOCKS5 Proxy | `/api/proxy?type=socks5&format=json` | ✅ 200 OK |
| Horikita SOCKS4 Proxy | `/api/proxy?type=socks4&format=json` | ✅ 200 OK |

## 🔧 Response Format

```json
{
  "status": 200,
  "total": 100,
  "last_check": "2024-01-15 14:30:00",
  "proxies": [
    "192.168.1.1:8080",
    "192.168.1.2:3128"
  ]
}
