FROM node

# Create app directory set as the working directory
WORKDIR /app

# Copy package.json into the container at /app
COPY package.json /app

# install the dependencies
RUN npm install

# copy the current directory contents into the container at /app
COPY . /app

# we want to expose port 80 to the outside world
EXPOSE 3000

# when we run the container, we want to start the server
CMD ["node","server.js"]


# steps to build and run the container
#  docker build -t app:latest .
#  docker run -p 3030:3000 app
#  Browser: http://localhost:3030/ => Hello from inside the very basic Node app!

# docker run --name=container-of-node-app app

# docker stop container-of-python-app container-of-node-app

# docker rm 5e35a3fe8ca1 b59410299ca3 a64902bc1407 2671296a361c
# docker rmi app


#  docker run --rm -p 3030:3000 app