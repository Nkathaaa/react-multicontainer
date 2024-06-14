FROM node:20-buster as builder
WORKDIR "/app"
COPY ./package.json ./
RUN npm set registry https://registry.yarnpkg.com && npm install
COPY . .
CMD ["npm","run","build"]
RUN ls -la /app
RUN ls -la /app/build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html