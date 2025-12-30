FROM node:14

# Create app directory set as the working directory
WORKDIR /app

# Copy package.json into the container at /app
COPY package.json .

# install the dependencies
RUN npm install

# copy the current directory contents into the container at /app
COPY . .

# we want to expose port 80 to the outside world
EXPOSE 80

# add volume here for permanent files [Path inside container - path outside contrainer]
# To  build: docker build -t feedback-node:volumes .
# To Run: docker run -p 3000:80 -d --name feedback-node:volumes --rm feedback-node:volumes
# TO Run: docker run -p 3000:80 -d --name feedback-app --rm feedback-node:volumes

# Stop contrianer: docker stop feedback-app
# To remove the image: docker rmi feedback-node:volumes
# This is anonymous volume only exists when container is running and disappear when we remove container (option --rm)
# To see volumes: docker volume ls
# VOLUME ["/app/feedback"] we will create named volume that will exists when container removed

# Start docker with name volume with:  docker run -p 3000:80 -d --name feedback-app --rm -v feedback:/app/feedback feedback-node:volumes
# name in host : folder path in container
# named vaolumes are not attached to container
# docker volume ls
# build container with the same volume: docker run -p 3000:80 -d --name feedback-app --rm -v feedback:/app/feedback feedback-node:volumes
# Important is that name volume name -> feedback

# when we run the container, we want to start the server
CMD ["node","server.js"]

# To  build: docker build -t feedback-node .
# To Run: docker run -p 3000:80 -d --name feedback-app --rm feedback-node
# http://localhost:3000/
# http://localhost:3000/feedback/good.txt
# docker stop feedback-app
# To Run: docker run -p 3000:80 -d --name feedback-app feedback-node
# docker stop feedback-app
# docker start feedback-app


# Note for anonymous volume it will exists if you run container without option -rm
# even you removed the containter after that
# You need to remove them manually using
# docker volume rm VOL_NAME
# or
# docker volume prune
