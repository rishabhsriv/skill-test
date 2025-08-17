FROM node:18-alpine AS build

ARG app_location='/usr/app'

WORKDIR ${app_location}

COPY package.json package-lock.json* ./
RUN npm install
COPY . .

FROM node:18-alpine

ARG app_location='/usr/app'

WORKDIR ${app_location}

COPY --from=build ${app_location} ./
EXPOSE 5007
CMD ["npm", "start"]
