## commands:

```docker
# make mongo run in localhost
docker run --name mongodb --rm -d  -p 27017:27017 mongo 

# dockerize backend
docker build -t goals-node .
docker run --name goals-backend --rm -d -p 80:80 goals-node

# dockerize frontend
docker build -t goals-react .
docker run --name goals-frontend --rm -d -p 3000:3000 -it goals-react

# stop all containers
docker ps | grep 'mongo'     
docker ps | grep 'goals'
docker stop mongodb  goals-backend  goals-frontend

# put them in the same network
docker network ls
docker network create goals-net
docker run --name mongodb --rm -d  --network goals-net mongo 

## we need to change database host to mongodb in backend hence we need to rebuild backend
docker build -t goals-node .
docker run --name goals-backend --rm -d --network goals-net goals-node

## we need to change in frontend hence we need to rebuild frontend in App.js change localhost to goals-backend
## we still need port here to able to access frontend from browser
docker build -t goals-react .
docker run --name goals-frontend --rm -d --network goals-net -p 3000:3000 -it goals-react
```