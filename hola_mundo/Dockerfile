FROM node:latest
WORKDIR ./hola_mundo
COPY index.js index.js
COPY package.json package.json
RUN npm install
EXPOSE 8080
ENTRYPOINT ["npm", "start"]