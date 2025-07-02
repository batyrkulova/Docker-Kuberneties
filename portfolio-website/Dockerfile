FROM node:20-alpine

WORKDIR /app

COPY . /app

RUN npm install

RUN npm run build

EXPOSE 3000

RUN chown -R node:node /app

USER node

CMD ["npm", "start"]