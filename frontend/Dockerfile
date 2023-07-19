FROM node:lts-alpine as builder

WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm install

COPY tsconfig.json tsconfig.json
COPY public public
COPY src src

RUN npm run build

FROM nginx:alpine

COPY --from=builder ./app/build /usr/share/nginx/html

CMD ["nginx", "-g", "daemon off;"]