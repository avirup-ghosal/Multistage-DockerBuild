# Dockerfile without multi-stage build
# FROM node:20

# WORKDIR /app

# COPY . .

# RUN npm install

# EXPOSE 3004

# CMD [ "node","index2.js" ]

# Dockerfile with multi-stage build
# Stage1: Build
FROM node:22-alpine AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Stage2: Production (Distroless)
FROM gcr.io/distroless/nodejs22-debian12

WORKDIR /app
COPY --from=build /app .

EXPOSE 3004

CMD ["index2.js"]
