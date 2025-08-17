FROM node:18-alpine AS build

ARG app_location='/usr/app'

WORKDIR ${app_location}

COPY package.json package-lock.json* ./
RUN npm install

COPY . .

RUN npm run build

FROM nginx:alpine

ARG app_location='/usr/app'

WORKDIR ${app_location}

RUN rm -rf /usr/share/nginx/html/*

COPY --from=build ${app_location}/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
