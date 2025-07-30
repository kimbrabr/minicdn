# MiniCDN

🚀 Лёгкий HTTP/2 CDN-сервер с RAM-кэшем, метриками и zero-copy передачей файлов.

## 📌 Цель

Создать высокопроизводительный CDN-сервер на C++20, который обслуживает статические файлы из RAM-кэша, с поддержкой HTTP/2 и мониторингом через Prometheus.

## ⚙️ Особенности

- Zero-copy: `sendfile()` или `io_uring` (файлы ≥64KB)
- LRU-кэш: lock-free, max 200 MB
- Поддержка HTTP/2 (через `nghttp2` или raw framing)
- Prometheus `/metrics` endpoint:
  - `minicdn_requests_total`
  - `minicdn_hit_ratio`
  - `minicdn_latency_ms`
- Работа с файлами из директории `./www`

## 🚀 Производительность

- ≥12 000 RPS (`wrk -t4 -c1000 -d30s`)
- RSS ≤200 MB при наборе файлов ~10 GB

<p align="center">
  <img src="assets/grafana-dashboard.gif" width="600" alt="Grafana dashboard">
</p>

## 📁 Структура

