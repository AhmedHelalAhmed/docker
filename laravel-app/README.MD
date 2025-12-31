## commends

```
docker-compose run --rm composer create-project --prefer-dist laravel/laravel:^8.0 .

docker-compose up -d server php mysql

docker-compose up -d server php mysql --build

docker-compose down -v

# after depends on it will run app dependencies
docker-compose up -d server

```

## sources

- https://hub.docker.com/_/mysql