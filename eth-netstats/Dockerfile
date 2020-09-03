# root/blockchain/eth-netstats/Dockerfile

# Ethereum Network Stats
# Support Visual interface for tracking ethereum network status.

FROM node:8-alpine

RUN apk add --update git

RUN git clone https://github.com/cubedro/eth-netstats

WORKDIR /eth-netstats

RUN npm install
RUN npm install -g grunt-cli
RUN grunt

EXPOSE 3001

CMD ["npm", "start"]
