## commends

```
docker-compose run --rm composer create-project --prefer-dist laravel/laravel:^8.0 .

docker-compose up -d server php mysql

docker-compose up -d server php mysql --build

docker-compose down -v

# after depends on it will run app dependencies
docker-compose up -d server

# force rebuild images
docker-compose up -d --build server

docker-compose run --rm artisan migrate

docker-compose run --rm npm install

```

## sources

- https://hub.docker.com/_/mysql