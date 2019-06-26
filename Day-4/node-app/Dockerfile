FROM node:9-alpine
WORKDIR '/var/www/app'
COPY . .
ENV REDIS_URL=redis://cache
ENV NODE_ENV=development
ENV PORT=3000
EXPOSE 3000
CMD sh -c 'npm i && node server.js'

