# #stage 1
# FROM node:19.5.0-alpine as node
# WORKDIR /app
# COPY . .
# RUN npm install
# RUN npm run build 
# #stage 2
# FROM nginx:alpine
# COPY --from=node /app/dist/login /usr/share/nginx/html

FROM johnpapa/angular-cli as angular-built
WORKDIR /usr/src/app
COPY package.json package.json
RUN npm install --prod
COPY . .
RUN ng build --prod

FROM nginx:alpine
LABEL author="ramesh gongura"
COPY --from=angular-built /usr/src/app/dist /usr/share/nginx/html
EXPOSE 80 443
CMD [ "nginx", "-g", "daemon off;" ]
