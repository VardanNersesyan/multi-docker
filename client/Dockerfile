FROM node:16-alpine AS builder
WORKDIR '/app'
COPY package.json .
COPY yarn.lock .
RUN yarn install
COPY . .
RUN yarn build

FROM nginx
EXPOSE 3000
COPY --from=builder /app/nginx/default.conf /etc/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
