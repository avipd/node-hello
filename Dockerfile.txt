FROM node:14-alpine
ENV NODE_ENV=production
WORKDIR /var/app
COPY . .
RUN npm install
EXPOSE 3000

CMD ["node", "index.js"]
