From node:18
WORKDIR /app
copy package*.json /app/
RUN npm install
COPY . .
CMD [ "npm","run","dev"]