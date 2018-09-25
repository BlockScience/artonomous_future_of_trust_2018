# Artonomous Future of Trust Demo
This is a simplified version of Artonomous meant to be demoed at the [Future of Trust Summit 2018](https://futureoftrust.eu/).  
[Front end](https://markusbkoch.github.io/fot2018/?autoRefresh=15)  
[Smart Contract](https://etherscan.io/address/0xfe9b5e8f7e8f6493f7d8532d915c9d53dffe9080)

## Goal
An interactive demo of a simplified version of Artonomous.

## Description
* Two hard coded generators; one active generator per turn; simple vote count determines the active generator (one transaction = one vote); any ethereum account can cast votes
* Art pieces are ERC-721 tokens (struct: timestamp; active generator at block of minting)
* When minted, the ERC-721 token is transferred to the creator of the smart contract (tokens will be transferred to a attendees in the future)
* Given the ID of an art piece, a client side art visualization code will:
  * query the Ethereum blockchain for the timestamp and generator of the corresponding ERC-721 token;
  * use the  as the seed of a random number generator;
  * create a piece of generative art with the timestamp and ID of the token as seed
    * each generator has its own characteristic collor pallete;
  * render the result on a web browser
* Screens at the event will showcase the art pieces.

## Acknowledgments
This demo is the result of few hours of development by an engineer with no experience in smart contract or front end development. We must thank 
* Axiom Zen for the Solidity code of [CryptoKitties](https://etherscan.io/address/0x06012c8cf97bead5deae237070f9587f8e7a266d#code), which was used as the base for this ERC-721 token; and
* Matt DesLauriers, whose amazing [Color-Wander](https://github.com/mattdesl/color-wander) is the core of our art generators.
