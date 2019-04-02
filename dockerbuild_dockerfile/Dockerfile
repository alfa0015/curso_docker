FROM node:latest
RUN apt-get update -y
RUN npm -g install yarn
WORKDIR /app
ENV NODE_ENV=development
COPY package.json .
COPY yarn.lock .
RUN yarn install
COPY . .
ENTRYPOINT [ "yarn" ]
CMD [ "serve", "--host=0.0.0.0", "--port=8080" ]
EXPOSE 8080