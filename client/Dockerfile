FROM node:alpine as builder 
#alias for the phase - as
WORKDIR /app

COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY  ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
#default command of nginx container will start up the server for us
