# Build stage
# pull node image
FROM node:20-alpine AS build

#create app directory
WORKDIR /app

# copy dependencies
COPY package*.json ./

#install packges
RUN npm install

# copy source code
COPY . .

# build the app
RUN npm run build


# Production stage
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]