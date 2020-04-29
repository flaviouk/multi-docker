FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install --prod
COPY . .
RUN npm run build
RUN rm -rf node_modules src

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
