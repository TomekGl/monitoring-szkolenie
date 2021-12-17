# Użycie docker-compose

## Przykładowe wywołanie `docker`

```bash
docker run nginx
```
może czasami ewoluować do:
```bash
docker run -p 8080:8080 -m 100M --memory-swap 100M -e NGINX_HOST=foo.com -e NGINX_PORT=8080 -v $(pwd)/html:/usr/share/nginx/html --name mynginx nginx
```

To samo można opisać:
```yaml
version: "2"

services:
  mynginx:
    image: nginx
    ports:
      - "8080:80"
    mem_limit: 100M
    environment:
      NGINX_HOST: foo.com
      NGINX_PORT: 8080
    volumes:
    - ./html:/usr/share/nginx/html
```

## Najczęściej używane polecenia

* Utworzenie środowiska
```bash
docker-compose up
docker-compose up -d
```

* Weryfikacja działąjących kontenerów
```bash
docker-compose ps
```

* Wyświetlanie logów środowiska
```bash
docker-compose logs
docker-compose logs -f
docker-compose logs <kontener>

* Zbudowanie obrazów do których istnieją odwołania do `Dockerfile` w `docker-compose.yml`
```bash
docker-compose build
```

* Usunięcie środowiska
```bash
docker-compose down
```

* Korzystanie z pliku konfiguracji innego niż `docker-compose.yml`
```bash
docker-compose -f <docker-compose-foo.yml> [polecenia]
```
