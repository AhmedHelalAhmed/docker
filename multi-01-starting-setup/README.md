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
cd backend
docker build -t goals-node .
docker run --name goals-backend --rm -d --network goals-net goals-node

## we need to change in frontend hence we need to rebuild frontend in App.js change localhost to goals-backend
## we still need port here to able to access frontend from browser
cd frontend
docker build -t goals-react .
docker run --name goals-frontend --rm -d --network goals-net -p 3000:3000 -it goals-react

## the issue App.js run in the brower not in container
## docker can not help us to automatic IP resolving to backend container react just run in the browser
## so it can not access backend via http://goals-backend/goals
## We should use http://localhost/goals as backend as this is what the browser understand
## this means we need to publish port 80 in backend container
## no need for network in frontend
docker build -t goals-react .
docker stop goals-frontend
docker run --name goals-frontend --rm -d -p 3000:3000 -it goals-react
docker stop goals-frontend
docker stop goals-backend
docker run --name goals-backend --rm -d -p 80:80 --network goals-net goals-node
```