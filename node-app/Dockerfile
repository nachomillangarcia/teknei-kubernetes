FROM node:16.10

WORKDIR /node-app

COPY . .

RUN npm install

EXPOSE 3000

ENV DEBUG=node-app:*

ENTRYPOINT ["npm", "start"]


