[Mapping the NFT revolution: market trends, trade networks, and visual features](https://www.nature.com/articles/s41598-021-00053-8.pdf)



Non Fungible Tokens (NFTs) are digital assets that represent artistic objects, encoded within smart contracts on a blockchain.

Here they analyzed data for 6 million trades and characterize the market.
The degree  moreover is used as feature to predict the price of NFT sales

###### Two networks are studied 

They consider the network of trades, where nodes are traders, a directed link from a trader to another exists if the former (the buyer) purchases at least one NFT from the latter (the seller). Each link has a weight corresponding to the total number of items that the buyer bought from the seller. (**strength**)
The strength is distributed as a power law with exponent = −1.85

The network of NFTs, is constructed such that nodes are NFTs and a directed link exists between two NFTs that are purchased “in sequence”, e.g. a link is created when a buyer purchases the former and then the latter, with no purchases between the two. 
This choice allows to understand the relations between NFT that are semantically similar, because they are bought by the same trader in approximately the same period of time.
The distribution of NFTs strength decays as a power law with exponent = −3.21
!![[nft_network.png]]