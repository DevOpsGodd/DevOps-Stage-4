# Development frontend with hot-reload
FROM node:14

WORKDIR /app

# Set HOST to 0.0.0.0 so it listens on all interfaces
ENV HOST=0.0.0.0
ENV PORT=8080

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 8080

CMD ["npm", "run", "dev"]
