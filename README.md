# edge-caddy

Shared Caddy for the VPS. Terminates TLS and reverse-proxies to every project's
containers over the external Docker network `edge`. Projects join `edge` with
prefixed aliases (e.g. `algo-web-frontend`) and add a file under `sites/`.

Deploy: `cp .env.example .env && docker compose up -d` (creates `edge`; do this
before bringing up any project that declares `edge` as external).
Reload after changing a site file: `docker compose exec caddy caddy reload --config /etc/caddy/Caddyfile`.
Host ports other than 80/443 must be listed under `ports:` in docker-compose.yml.
