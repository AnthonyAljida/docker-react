FROM node:22-alpine as builder

WORKDIR /usr/app
RUN npm install -g pnpm

COPY ./package.json ./
RUN pnpm install

COPY ./ ./
RUN pnpm run build

FROM nginx
COPY --from=builder ./usr/app/dist ./usr/share/nginx/html
