FROM node:lts-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
ENV MONGO_URI=""
EXPOSE 9000
CMD ["npm", "start"]
