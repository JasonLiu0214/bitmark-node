# Bitmark Node

## Introduction

Bitmark node is the easiest way for anyone to join the Bitmark network as a fully-validating peer. You can create, verify, mine Bitmark transactions and get possible reward.  A Bitmark node contains the following programs:

 - bitmarkd: Main program
 - prooferd: A tool to mine Bitmark blocks
 - bitmark-wallet: A wallet for transactions (currently support Bitcoin & Litecoin)
 - bitmark-cli: Command line interface to bitmarkd
 - bitmark-webui: A webpage user interface for basic control of Bitmark node


## Bitmark Blockchain

Bitmark provides two different chains for a Bitmark node to join in. They are `testing`, `bitmark`, which refer to testnet & livenet respectively. In order to finish a transaction, you need to send Bitcoin or Litecoin to the proofing(mining) Bitcoin or Litecoin address, which can be configured in bitmark-webui.

In order to finish a transaction, you need to send bitcoin or litecoin to the proofing(mining) address of the bitcoin or litecoin which can be configured in the proofing block via web ui.

Please note: There are default Bitcoin & Litecoin addresses in both `testing` & `bitmark` chains. Please set your own value if you want to validate a transfer via your own Bitcoin/Litecoin addresses.

Here is a table that shows correlations between different blockchains.

|   Bitmark Blockchain  |   Bitcoin Blockchain |  Litecoin Blockchain |
|    :---:     |    :---:    |    :---:   |
|   testing    |   testnet   |   testnet  |
|   bitmark    |   livenet   |   livenet  |

## Installation

To run a Bitmark node, you need to have basic understanding of Docker and are able to setup Docker environment

### Install Docker

Go to Docker website to download and install: https://www.docker.com

### Fetch Bitmark Node in Docker

After you successfully installed docker, use the following command to pull `bitmark-node` image:

```
$ docker pull bitmark/bitmark-node
```

When the Docker container has been started up for the first time, it will generate required keys for you inside the container. A web server is running inside the container and is able to control Bitmark services.

### Run Bitmark Node

```
$ docker run -d --name bitmarkNode -p 9980:9980 \
-p 2136:2136 -p 2135:2135 -p 2130:2130 \
-e PUBLIC_IP=54.249.99.99 \
bitmark/bitmark-node
```

The configurable options are:

  - Enviornments:
    - PUBLIC_IP: public address to announce
    - BTC_ADDR: bitcoin address for proofing
    - LTC_ADDR: litecoin address for proofing
  - Ports:
    - 2130 - Port of RPC server
    - 2135, 2136 - Port of peering
    - 9980 - Port of web server
  - Volume:
    - /.config/bitmark-node/bitmarkd/bitmark/data - chain data for bitmark
    - /.config/bitmark-node/bitmarkd/testing/data - chain data for testing

### Web UI

Open web browser and go to  bitmark-webui (PUBLIC_IP:9980) to check  or configure Bitmark blockchain status. 

### Docker Compose

In the folder, there is a `docker-compose.yml` file that gives you an example of how to configurate correctly to make bitmark-node up-and-run.
