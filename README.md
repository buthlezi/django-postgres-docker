
# Dockerize Django with Postgres, Gunicorn and Nginx

### Development

```sh
$ docker-compose up -d --build 
(OR)
$ docker-compose -f docker-compose.yml up -d --build
```
- 
- 
(for Linux use `docker-compose` NOT `docker compose` !!)
- 
- 
Test app at: [http://localhost:8000](http://localhost:8000). The "app" folder is mounted into the container and your code changes apply automatically.

run django terminal command example:
```sh
docker-compose exec web python manage.py migrate
```
## cleaning up afterwards
docker-compose down -v
docker-volume prune

(for Linux use `docker-compose` NOT `docker compose` !!)

### Production


```sh
docker-compose -f docker-compose.prod.yml up -d --build
docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear
```
(for Linux use `docker-compose` NOT `docker compose` !!)


Test app at: [http://localhost:1337](http://localhost:1337). Folders are not mounted, image needs to be rebuilt.

`ERROR:` The Compose file `'./docker-compose.prod.yml'` is invalid because: `services.nginx.ports` contains an invalid type, it should be an array
