# Artonomous Future of Trust Demo

This is a version of Artonomous meant to be demoed at the [Future of Trust Summit 2018](https://futureoftrust.eu/).

## Goal
An interactive demo of a version of Artonomous running for 24 hours on September 25th.

## Description
* Two hard coded generators; one active generator per turn; simple vote count determines the active generator (one transaction = one vote); any ethereum account can cast votes
* Art pieces are ERC-721 tokens (struct: block number; active generator at block of minting)
* When minted, the ERC-721 token is transferred to a random address of a set of addresses (paper wallets handed out to event attendees)
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
