# Build Phase
FROM node:alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
# This creates a build dir in /app folder
RUN npm run build

# Run phase
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html
