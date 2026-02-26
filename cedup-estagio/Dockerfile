# Build stage
FROM node:20 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Run stage
FROM node:20

WORKDIR /app

COPY --from=builder /app/build ./build
COPY --from=builder /app/package*.json ./
RUN npm install --omit=dev

EXPOSE 5173

# SvelteKit com node-adapter geralmente roda na porta 3000, mas o Vite dev usa 5173.
# Se estiver usando @sveltejs/adapter-node, precisamos configurar a porta.
ENV PORT=5173
CMD ["node", "build"]
