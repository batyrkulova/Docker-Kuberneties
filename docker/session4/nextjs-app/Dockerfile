#Stage1
#Install dependencies
FROM node:20-alpine AS deps 

WORKDIR /app

COPY package*.json ./

#Create node modules folder
RUN npm install

#Stage2
#Build and Compile
FROM node:20-alpine AS builder

WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules

COPY . . 

RUN npm run build

#Stage3

FROM node:20-alpine AS final 

WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules

COPY --from=builder /app/.next ./next

COPY --from=builder /app/public ./public

COPY --from=builder /app/package.json ./

COPY --from=builder /app/next.config.js ./

RUN chown -R node:node /app

USER node 

EXPOSE 3000

CMD ["npm", "start"]