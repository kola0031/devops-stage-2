FROM node:14-alpine as build-stage

WORKDIR /app

COPY package.json .

RUN npm install

RUN npm i -g serve

COPY . .

RUN npm run build
FROM nginx
COPY --from=build-stage .  /usr/share/nginx/html

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]