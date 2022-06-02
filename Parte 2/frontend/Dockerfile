
FROM node:12.18.2 as build

WORKDIR /frontend

COPY *.json /frontend/

RUN npm install -f 

COPY . .

EXPOSE 3000

RUN npm run build

FROM nginx

COPY --from=build /assets/bundles /usr/share/nginx/html