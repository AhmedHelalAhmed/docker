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


# starting mongodb again loss the data we stored on it
docker stop mongodb
docker run --name mongodb --rm -d  --network goals-net mongo 

# save the data using named volume
docker stop mongodb
docker run --name mongodb -v data:/data/db --rm -d  --network goals-net mongo 


# use authentication in mongodb
docker stop mongodb
## you must delete the volume first with name data to able to set authentication
docker volume rm data
docker run --name mongodb -v data:/data/db --rm -d  --network goals-net -e MONGO_INITDB_ROOT_USERNAME=ahmed -e MONGO_INITDB_ROOT_PASSWORD=secret mongo 
## now we need to update backend to use authentication
docker stop goals-backend
docker build -t goals-node .
docker run --name goals-backend --rm -d -p 80:80 --network goals-net goals-node
## see 
# https://hub.docker.com/_/mongo
# https://stackoverflow.com/questions/40608669/what-does-authsource-means-in-mongo-database-url

# live source code update
docker stop goals-backend
docker run --name goals-backend -v /Users/ahmedhelal/mypc/projects/docker/multi-01-starting-setup/backend:/app -v logs:/app/logs -v /app/node_modules --rm -d -p 80:80 --network goals-net goals-node
docker ps | grep 'backend'
# use nodemon to live reload
docker stop goals-backend
docker build -t goals-node .
docker run --name goals-backend -v /Users/ahmedhelal/mypc/projects/docker/multi-01-starting-setup/backend:/app -v logs:/app/logs -v /app/node_modules --rm -d -p 80:80 --network goals-net goals-node
# check logs to ensure we use nodemon
docker logs goals-backend
# try to change source code in backend and see logs to ensure it live reload
docker logs goals-backend

# let read database data from env
# change in dockerfile and app.js
docker stop goals-backend
docker build -t goals-node .
# set env variable in docker run for username
docker run --name goals-backend -v /Users/ahmedhelal/mypc/projects/docker/multi-01-starting-setup/backend:/app -v logs:/app/logs -v /app/node_modules -e MONGODB_USERNAME=ahmed --rm -d -p 80:80 --network goals-net goals-node
docker logs goals-backend

# live source code for frontend
docker stop goals-frontend
docker run -v /Users/ahmedhelal/mypc/projects/docker/multi-01-starting-setup/frontend/src:/app/src --name goals-frontend  --rm -d -p 3000:3000 -it goals-react

# add .dockerignore to frontend folder to avoid uploading node_modules
docker stop goals-frontend
docker build -t goals-react .
docker run -v /Users/ahmedhelal/mypc/projects/docker/multi-01-starting-setup/frontend/src:/app/src --name goals-frontend  --rm -d -p 3000:3000 -it goals-react
```