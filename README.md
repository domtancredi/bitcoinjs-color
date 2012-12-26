Bitcoinjs-color
===============

Steps to Setup and Run a Script:

    1. make sure the mongo daemon is running (i.e. 'mongod')
    2. run the bitcoinjs-color server (i.e. bitcoinjs run)
    3. run the bitcoinjs-color query (i.e. node app.js)
    4. open a seperate terminal within the project 
    5. run the javascript test (i.e. node async.js)
    

Based on: https://github.com/bitcoinjs/node-bitcoin-explorer

Tool to check colored bitcoin on bitcoinjs

Installation in Ubuntu:

after fresh install

    sudo apt-get update

Dependencies

    sudo apt-get install build-essential python2.7 pkg-config libssl-dev git

Node v0.8.8

    git clone git://github.com/joyent/node.git
    cd node
    git checkout v0.8.8
    ./configure
    make
    sudo make install

Install bitcoinJS:

    sudo npm install -g bitcoinjs --unsafe-perm

    mkdir /home/ubuntu/.bitcoinjs
    cp /usr/local/lib/node_modules/bitcoinjs/daemon/settings.example.js /home/ubuntu/.bitcoinjs/settings.js

Install bitcoinJS-color:

    cd ~

    git clone https://github.com/0i0/bitcoinjs-color.git

    cd bitcoinjs-color/
    sudo npm link bitcoinjs
    sudo npm install

    cp ~/bitcoinjs-color/node_modules/bitcoinjs/daemon/settings.example.js ~/bitcoinjs-color/node_modules/bitcoinjs/daemon/settings.js

Edit ~/bitcoinjs-color/node_modules/bitcoinjs/daemon/settings.js
Change the following:

    cfg.jsonrpc.enable = true;
    cfg.jsonrpc.password = "admin";

This is for Amazon AWS to work on port 80

    sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 3333

Running

    bitcoinjs start
    node app.js
    
Running bitcoin-tx-spent-db
  1. kick off mongo daemon (anywhere): "run mongod" 
  2. setup bitcoinjs-server (in bitcoinjs-color): "node app.js"
  2. initialize db (in bitcoin-tx-spent-db), "node app.js create"