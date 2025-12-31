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
```