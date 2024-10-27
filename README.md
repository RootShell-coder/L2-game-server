# Lineage2 Essence Seven Signs (Local server)

> For informational purposes only

_If this violates someone's rights, you know where to go._

Need `WSL` to run this. You'll have to google how to add this to your windows. If you've successfully done this, then create a file in WSL called `docker-compose.yml` and write this into it

```yml
---
services:
  game:
    image: "ghcr.io/rootshell-coder/l2-game-server:latest"
    ports:
      - "127.0.0.1:7777:7777"
      - "127.0.0.1:2106:2106"
    restart: "unless-stopped"
    deploy:
      resources:
        limits:
          cpus: "3.0"
          memory: 6G
        reservations:
          cpus: "3.0"
          memory: 6G
```

To run, execute `docker compose up -d`, to stop `docker compose down` _Always starts from the very beginning after restart_
