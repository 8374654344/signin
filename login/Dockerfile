#stage 1
FROM node as node
WORKDIR /app
COPY package.json package.json
RUN npm install
COPY . .
RUN npm run build 
#stage 2
FROM nginx:alpine
COPY --from=node /app/dist/login /usr/share/nginx/html

# FROM johnpapa/angular-cli as angular-built
# WORKDIR /app
# COPY . .
# RUN npm install 
# COPY . .
# RUN ng build 
# FROM nginx:alpine
# LABEL author="ramesh gongura"
# COPY --from=angular-built /usr/src/app/dist /usr/share/nginx/html
# EXPOSE 80 443
# CMD [ "nginx", "-g", "daemon off;" ]
