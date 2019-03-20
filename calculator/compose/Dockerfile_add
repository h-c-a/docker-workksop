FROM node:8

WORKDIR /root/
RUN npm install -g express
ENV NODE_PATH=/usr/local/lib/node_modules/
COPY add2.js .
CMD [ "node", "add2.js"]