FROM node:20-alpine AS first 
WORKDIR /app
COPY package*.json ./
RUN npm install

FROM node:20-alpine AS second
WORKDIR /app
COPY --from=first /app/node_modules ./node_modules 
COPY . . 
RUN npm run build

FROM node:20-alpine AS third 
WORKDIR /app
COPY --from=first /app/node_modules ./node_modules
COPY --from=second /app/.next ./next
COPY --from=second /app/public ./public
COPY --from=second /app/package*.json ./
COPY --from=second /app/next.config.js ./
RUN chown -R node:node /app
USER node
EXPOSE 3000
CMD ["npm", "start"]