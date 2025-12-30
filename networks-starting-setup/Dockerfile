FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

CMD ["node", "app.js"]

# docker build -t favorites-node .
# docker run --name favorites -d --rm -p 3000:3000 favorites-node
# run it without -d to find the issue
# docker run --name favorites  --rm -p 3000:3000 favorites-node
# the issue is the database connection

# docker run -d  --name mongodb mongo
# docker container inspect mongodb - to get ip address


# docker stop mongodb
# docker rm mongodb
# you have to create the network
# docker network create favorites-net
# docker run -d  --name mongodb --network favorites-net mongo
# docker network ls
# docker build -t favorites-node .
# docker run --name favorites --network  favorites-net --rm -p 3000:3000 favorites-node
# Note: the two containers must be on the same network

# Docker Network Drivers
# docker network create --driver bridge my-net
# host: For standalone containers, isolation between container and host system is removed (i.e. they share localhost as a network)
# overlay: Multiple Docker daemons (i.e. Docker running on different machines) are able to connect with each other. Only works in "Swarm" mode which is a dated / almost deprecated way of connecting multiple containers
# macvlan: You can set a custom MAC address to a container - this address can then be used for communication with that container
# none: All networking is disabled.
# Third-party plugins: You can install third-party plugins which then may add all kinds of behaviors and functionalities