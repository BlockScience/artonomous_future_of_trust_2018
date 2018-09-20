# Artonomous Future of Trust Demo

This is a version of Artonomous meant to be demoed at the [Future of Trust Summit 2018](https://futureoftrust.eu/).

## Goal
An interactive demo of a version of Artonomous running for 24 hours on September 25th.

## Description
* Two hard coded generators; one active generator per turn; simple vote count determines the active generator (one transaction = one vote); any ethereum account can cast votes
* Art pieces are ERC-721 tokens (struct: block number; active generator at block of minting)
* When minted, the ERC-721 token is transferred to a random address of a set of addresses
* New art pieces are minted every 60 blocks 
* Given the ID of an art piece, a client side art visualization code will:
  * query the Ethereum blockchain for the block number and generator of the corresponding ERC-721 token;
  * query the Ethereum blockchain for the corresponding block hash;
  * use that hash as the seed of a random number generator;
  * select a random image from a pool of images on a server
  * apply a watermark and a filter and/or an animation to that image
    * each generator has its own characteristic watermark/filter/animation; 
    * parameters of the animation/filter are randomly selected (same seed as before);
  * render the result on a web browser
* Screens at the event will show live data of vote count of each generator and art piece created.

## Key Directory Structure (same as ethberlin repo this was forked from)
* `artnonmous-subgraph/`: Holds the subgraph for thegraph.com's engine
* `graph-node-container/`: Custom scripts and runtime configuration (in docker) to run the graph-node-container locally
* `src/`: Holds the front-end web application source code
* `contracts/`: Holds the solidity contracts that run the backbone of the application 

## Deployment (same as ethberlin repo this was forked from)
* To develop the frontend: `docker-compose up` in the root directory
* To build the frontend: `yarn build`.
* To build the graph-node-container dep containers: 
  * `cd graph-node-container && docker-compose`
* To generate the ipfs 
  * First, the graph-node-container cluster needs to be running, or at least IPFS
  * Second, `node genAbi.js` needs to be run from the root directory if any of the solidity contracts are changed, after they have been compiled to `build/`
  * Third, `yarn build-ipfs` builds the subgraph code from the yaml manifest and the graphql and bootstrap typescript files into a ipfs hash, which is printed upon completion. This hash is needed to run the graph-node-container.
* To run the `graph-node-container`, with the docker images for postgres and ipfs running, run `./run.sh IPFS_SUBGRAPH_HASH` which starts the server on localhost:8000.
* Finally, the frontend graphql server can be configured in `src/apollo.js` and the ipfs endpoint in `src/fsapi.js`.
