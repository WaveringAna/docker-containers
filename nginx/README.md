```bash
docker-compose up
```

spin up any proxied docker container with env VIRTUAL_HOST, VIRTUAL_PORT, LETSENCRYPT_HOST

```bash
docker run --detach \
    --name grafana \
    --env "VIRTUAL_HOST=othersubdomain.yourdomain.tld" \
    --env "VIRTUAL_PORT=3000" \
    --env "LETSENCRYPT_HOST=othersubdomain.yourdomain.tld" \
    --env "LETSENCRYPT_EMAIL=mail@yourdomain.tld" \
    grafana/grafana
```

docker-compose.yml
```yml
version: '3.3'
services:
  grafana:
    contaienr_name: grafana
    ports:
      - '3000:3000'
    environment:
      - VIRTUAL_HOST=othersubdomain.yourdomain.tld
      - VIRTUAL_PORT=3000
      - LETSENCRYPT_HOST=othersubdomain.yourdomain.tld
      - LETSENCRYPT_EMAIL=mail@yourdomain.tld
    image: 'grafana/grafana'
    network_mode: bridge
```
