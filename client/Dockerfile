FROM node:12

WORKDIR /opt/app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /opt/app/build /usr/share/nginx/html 