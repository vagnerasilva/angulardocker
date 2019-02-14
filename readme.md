Dockerfile client:
FROM node:10.15.1
WORKDIR /app
COPY package.json /app
RUN npm install
RUN npm install -g @angular/cli@7.3.1
COPY . /app
EXPOSE 4200
CMD ng serve --host 0.0.0.0 --port 4200

Dockerfile server:
FROM node:10.15.1
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app
RUN npm install
RUN npm install -g nodemon --quiet
COPY . .
EXPOSE 3000
CMD ["npm", "start"]

docker-compose:
version: '3'
services:
front:
image: contacts.client
build: contact-spa
command: npm start
ports:
- '4200:4200'
links:
- back
back:
image: contacts.backend
build: contact-api
command: npm start
ports:
- '3000:3000'
links:
- db
db:
image: mongo
ports:
- '27017:27017'
restart: always



Criar imagens primeiro 
docker build -t clients .

docker build -t clientFront .

docker build -t serverBackend .
docker run -d --name container_name image_name