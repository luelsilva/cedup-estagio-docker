FROM node:20

WORKDIR /app

COPY package*.json ./

RUN npm install --omit=dev

COPY . .

# A API usa a porta 3000 por padrão no .env
EXPOSE 3000

CMD ["npm", "start"]
