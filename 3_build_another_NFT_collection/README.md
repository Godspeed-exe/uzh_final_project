## NFT Collections

In our hands on example we created a fairly simple NFT example. You can use this as a foundation to create your own NFT's. I would suggest to use a persistent storage (like MySQL or SQLlite) to:

- store the assets with a status (default: 0)
- build a processing script that reads the assets from the database and constructs transactions to mint them.
- update the status of successfully created assets. Transactions might fail if you are not waiting in between transactions or if you are not using transaction chaining.


Our example NFT's are based on [CIP25](https://cips.cardano.org/cip/CIP-0025) metadata standard. This is known as "static metadata".

Cardano also has a "Dynamic Metadata Standard" called [CIP68](https://cips.cardano.org/cip/CIP-0068). In this setup metadata is stored on UTXO level, since you can spend a UTXO you can also update the metadata. This is useful for gaming characters or renewable subscriptions, for example.