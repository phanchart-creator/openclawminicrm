FROM node:22-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build && \
    cp -r .next/static .next/standalone/.next/static && \
    cp -r public .next/standalone/public 2>/dev/null || true

EXPOSE 3001

ENV PORT=3001
ENV HOSTNAME=0.0.0.0
CMD ["node", ".next/standalone/server.js"]
