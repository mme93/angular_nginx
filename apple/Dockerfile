FROM node:14.15-alpine as build

WORKDIR /usr/src/app
COPY . ./
RUN npm install
RUN npm run ng build --prod

FROM nginx:1.15.2-alpine

COPY --from=build /usr/src/app/dist/angular_nginx-app /var/www
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 3000
ENTRYPOINT ["nginx","-g","daemon off;"]
