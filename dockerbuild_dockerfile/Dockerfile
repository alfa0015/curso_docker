FROM node:alpine
RUN npm -g install yarn
WORKDIR /app
ENV NODE_ENV=development
COPY . .
RUN yarn install
ENTRYPOINT [ "yarn" ]
CMD [ "serve", "--host=0.0.0.0", "--port=8080" ]
EXPOSE 8080