# Step #1 and we call it - build
FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# Export listening port for external access
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# Copy file from step #1 - build
COPY --from=builder /app/build /usr/share/nginx/html              