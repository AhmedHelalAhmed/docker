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

VOLUME ["/app/feedback"]

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
