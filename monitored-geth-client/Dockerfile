# root/blockchain/moniroted-geth-client/Dockerfile

# Ethereum Go node client
# Official Golang implementation of the Ethereum protocol.
FROM ethereum/client-go

RUN apk add --update git bash nodejs nodejs-npm perl

# Backend service which runs along with ethereum and tracks the network status
# and connects through WebSockets to eth-netstats to feed information
RUN cd /root &&\
    git clone https://github.com/cubedro/eth-net-intelligence-api &&\
    cd eth-net-intelligence-api &&\
    npm install &&\
    npm install -g pm2

ADD start.sh /root/start.sh
ADD app.json /root/eth-net-intelligence-api/app.json
RUN chmod +x /root/start.sh

ENTRYPOINT /root/start.sh
