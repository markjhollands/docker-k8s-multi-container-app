FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# On deployment Amazon Elastic Beanstalk will look at the following expose
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.f/default.conf
COPY --from=builder /app/build /usr/share/nginx/html