# Choosing a base image
FROM node:14.15.4-alpine

# copy your application files
# to the /usr/app directory inside the container
WORKDIR /usr/app
COPY . .

# build your project
ENV NODE_ENV production
RUN npm run build

# here we go
CMD [ "npm", "start" ]

# docker build -t hello-next .
# docker run -it --rm -p 3000:3000 --name hello-next-running hello-next
