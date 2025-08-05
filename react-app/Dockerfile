# -- build stage -------------------------------------------------
FROM node:20-alpine AS build
WORKDIR /app
COPY . .
RUN npm ci && npm run build     # создаёт production-сборку в /app/build

# -- runtime stage -----------------------------------------------
FROM nginx:1.27.0-alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]
