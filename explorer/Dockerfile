# root/blockchain/explorer/Dockerfile

# Ethereum Block Explorer
# Support for checking ETH transactions, information on blocks, smart contracts with visual interface
FROM node:8.10.0

RUN git clone https://github.com/carsenk/explorer.git

WORKDIR /explorer

RUN sed 's/-a localhost -p 8000/-a 0.0.0.0 -p 8000/g' package.json > pkg.json
RUN rm -f package.json
RUN mv pkg.json package.json

RUN npm install
RUN node_modules/.bin/bower install --force-latest --allow-root

ARG GETH_HOSTNAME
ARG GETH_RPCPORT

RUN sed "s/var GETH_HOSTNAME\t= \"localhost\";/var GETH_HOSTNAME\t=\"${GETH_HOSTNAME}\";/g" /explorer/app/app.js > /explorer/app/apptmp.js
RUN sed "s/var GETH_RPCPORT  \t= 8545;/var GETH_RPCPORT  \t= ${GETH_RPCPORT};/g" /explorer/app/apptmp.js > /explorer/app/app.js
RUN rm -f /explorer/app/apptmp.js

EXPOSE 8000

CMD ["npm", "start"]              
