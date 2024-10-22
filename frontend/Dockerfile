FROM node:18.17.0
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
ENV REACT_APP_BACKEND_URL=http://localhost:80
CMD ["npm", "start"]