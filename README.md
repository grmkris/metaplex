test
<p align="center">
  <a href="https://metaplex.com">
    <img alt="Metaplex" src="https://metaplex.com/meta.svg" width="250" />
  </a>
</p>

Metaplex is a protocol built on top of Solana that allows:

- **Creating/Minting** non-fungible tokens;
- **Starting** a variety of auctions for primary/secondary sales;
- and **Visualizing** NFTs in a standard way across wallets and applications.

Metaplex is comprised of two core components: an on-chain program, and a self-hosted front-end web3 application.

## In Depth Developer's Guide

If you want to deep dive on the Architecture, you can do so here:

https://docs.metaplex.com/

## Installing

Clone the repo, and run `yarn start` to deploy.

```bash
$ git clone https://github.com/metaplex-foundation/metaplex.git
$ cd metaplex
$ cd js
$ yarn install
$ yarn bootstrap
$ yarn start
```

## Rust Programs

The Rust programs will soon be added to this repo with JavaScript
bindings that allow interactivity.

## Community

We have a few channels for contact:

- [Discord](https://discord.gg/metaplex)
- [@metaplex](https://twitter.com/metaplex) on Twitter
- [GitHub Issues](https://github.com/metaplex-foundation/metaplex/issues)

# Protocol

## Non-fungible tokens

Metaplex's non-fungible-token standard is a part of the Solana Program Library (SPL), and can be characterized as a unique token with a fixed supply of 1 and 0 decimals. We extended the basic definition of an NFT on Solana to include additional metadata such as URI as defined in ERC-721 on Ethereum.

Below are the types of NFTs that can be created using the Metaplex protocol.

### **Master Edition**

A master edition token, when minted, represents both a non-fungible token on Solana and metadata that allows creators to control the provenance of prints created from the master edition.

Rights to create prints are tokenized itself, and the owner of the master edition can distribute tokens that allow users to create prints from master editions. Additionally, the creator can set the max supply of the master edition just like a regular mint on Solana, with the main difference being that each print is a numbered edition created from it.

A notable and desirable effect of master editions is that as prints are sold, the artwork will still remain visible in the artist's wallet as a master edition, while the prints appear in the purchaser's wallets.

### **Print**

A **print** represents a copy of an NFT, and is created from a Master Edition. Each print has an edition number associated with it.

Usually, prints are created as a part of an auction that has happened on Metaplex, but they could also be created by the creator manually.

For limited auctions, each print number is awarded based on the bid placement.

Prints can be created during [Open Edition](#open-edition) or [Limited Edition](#limited-edition) auction.

### Normal NFT

A normal NFT (like a Master Edition) when minted represents a non-fungible token on Solana and metadata, but lacks rights to print.

An example of a normal NFT would be an artwork that is a one-of-a-kind that, once sold, is no longer within the artist's own wallet, but is in the purchaser's wallet.

## Types of Auctions

Metaplex currently supports four types of auctions that are all derived from English auctions.

Basic parameters include:

- Auction start time
- Auction end time
- Reservation price

Additionally, Metaplex includes a novel concept of the participation NFT. Each bidding participant can be rewarded a unique NFT for participating in the auction.

The creator of an auction also has the ability to configure a minimal price that should be charged for redemption, with the option to set it as "free".

### Single Item

This type of auction can be used to sell normal NFTs and re-sell Prints, as well as the sale of Master Edition themselves (and the associated printing rights) if the artist so wishes. While this last behavior is not exposed in the current UI, it does exist in the protocol.

### Open Edition

An open edition auction requires the offering of a Master Edition NFT that specifically has no set supply. The auction will only create Prints of this item for bidders: each bidder is guaranteed to get a print, as there are no true "winners" of this auction type.

An open edition auction can either have a set fixed price (equivalent to a Buy Now sale), can be set to the bid price (Pay what you want), or can be free (Make any bid to get it for free).

### Limited Edition

For a limited edition auction, a Master Edition NFT (of limited or unlimited supply) may be provided to the auction with a number of copies as the set amount of winning places.

For each prize place, a Print will be minted in order of prize place, and awarded to the winning bidder of that place.

For example, the first place winner will win Print #1; the second place winner Print #2; and so on.

It is required for limited supply NFTs that there is at least as much supply remaining as there are desired winners in the auction.

### Tiered Auction

A tiered auction can contain a mix of the other three auction types as winning placements. For instance, the first place winner could win a Print of Limited Edition NFT A, while the second-place winner could win Normal NFT, and so on. Additionally, all participants who did not win any place could get a Participation NFT Print from a Master Edition (if the Master Edition had no supply limit).

## Royalties

Metaplex can seamlessly create on-chain artist splits that remove the awkwardness out of collaboration.

Tag each collaborator, set custom percentages, and you’re off to the races. Each NFT can also be minted with configurable royalty payments that are then sent automatically back to the original creators whenever an artwork is resold on a Metaplex marketplace in the future.

## Storefronts

Metaplex's off-chain component allows creators to launch a custom storefront, similar to Shopify or WordPress. This open-source project provides a graphical interface to the on-chain Metaplex program, for creators, buyers, and curators of NFTs. The design and layout of storefronts can be customized to suit the needs of the entity creating it, either as a permanent storefront or an auction hub for a specific auction or collection.

All identification on the Storefront is based on wallet addresses. Creators and store admins sign through their wallets, and users place bids from connected wallets. Custom storefronts allow creators to create unique experiences per auction. Additionally, the Metaplex Foundation is working on multiple partnerships that will enable building immersive storefronts using VR/AR.



### Added by me
#### Commands
`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts`
`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts upload ./assets --env devnet --keypair ~/.config/solana/devnet.json`
`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts verify --env devnet --keypair ~/.config/solana/devnet.json`

`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts verify_token_metadata ./assets --env devnet --keypair ~/.config/solana/devnet.json`

`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts create_candy_machine --env devnet --keypair ~/.config/solana/devnet.json --price 1 --sol-treasury-account 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr`

`ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts update_candy_machine --env devnet --keypair ~/.config/solana/devnet.json --price 1 --date "01 Oct 2021 16:12:00 GMT"`
#### Output
```
➜  cli git:(master) ✗ solana-keygen new --outfile ~/.config/solana/devnet.json
Generating a new keypair

For added security, enter a BIP39 passphrase

NOTE! This passphrase improves security of the recovery seed phrase NOT the
keypair file itself, which is stored as insecure plain text

BIP39 Passphrase (empty for none): 

Wrote new keypair to /Users/kristjangrm/.config/solana/devnet.json
=======================================================================
pubkey: 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr
=======================================================================
Save this seed phrase and your BIP39 passphrase to recover your new keypair:
you pink pottery foil switch raw rate night awkward rabbit client jeans
=======================================================================
```

```
➜  cli git:(master) ✗ ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts upload ./assets --env devnet --keypair ~/.config/solana/devnet.json
Beginning the upload for 2 (png+json) pairs
started at: 1633100752102
wallet public key: 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr
Processing file: 0
initializing config
initialized config for a candy machine with publickey: DmEHajTUu66qNMLXGZdDXCmfk2Efpu5eSF2s1hcuHDfu
Writing indices 0-1
Done. Successful = true.
ended at: 2021-10-01T15:06:36.637Z. time taken: 00:00:44
```

```
➜  cli git:(master) ✗ ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts create_candy_machine --env devnet --keypair ~/.config/solana/devnet.json --price 1 --sol-treasury-account 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr
wallet public key: 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr
create_candy_machine finished. candy machine pubkey: EwUzW8yLWM1Wb2XRyMgMgDuwzXzR73bwmTVmXDtnzaQc
```

```
➜  cli git:(master) ✗ ts-node /Users/kristjangrm/Code/github-com/metaplex/js/packages/cli/src/candy-machine-cli.ts update_candy_machine --env devnet --keypair ~/.config/solana/devnet.json --price 1 --date "01 Oct 2021 16:12:00 GMT"
wallet public key: 7WQEbdkSYPUrYc8aUuyKH6ADpEpDJo4ryx9sZGbMfQqr
 - updated startDate timestamp: 1633104720 (01 Oct 2021 16:12:00 GMT)
 - updated price: 1000000000 lamports (1 SOL)
updated_candy_machine finished 2kkKhMRndXLmPngNVn8iyusphCZYHpCPMXn7EyHtna6Xwp887cFLyPxYSd5N4EGpS7mv5nTuR5WHLvCwvmRDNV7y
```
