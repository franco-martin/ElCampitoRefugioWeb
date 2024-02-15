FROM node:18.17.1-buster as build
WORKDIR /app
COPY package.json /app/
RUN npm install
COPY . /app/
RUN npm run build

FROM node:18.17.1-buster
WORKDIR /app
COPY package.json /app/
COPY --from=build /app/dist/ /app/
COPY --from=build /app/node_modules /app/node_modules/
CMD ["node", "app.js"]