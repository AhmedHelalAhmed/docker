FROM node:14-alpine

WORKDIR /app

# CMD npm init

# Commends:
# docker build -t node-util .

# docker run node-util npm init

## You should use interactive mode
# docker run -it node-util npm init

## mirror the folder to local folder
# docker run -it -v /Users/ahmedhelal/mypc/projects/docker/utility-containers:/app node-util npm init

ENTRYPOINT ["npm"]

# with option ENTRYPOINT we can do that
# docker build -t mynpm .
# docker run -it -v /Users/ahmedhelal/mypc/projects/docker/utility-containers:/app mynpm init
# docker run -it -v /Users/ahmedhelal/mypc/projects/docker/utility-containers:/app mynpm install
# docker run -it -v /Users/ahmedhelal/mypc/projects/docker/utility-containers:/app mynpm install express --save