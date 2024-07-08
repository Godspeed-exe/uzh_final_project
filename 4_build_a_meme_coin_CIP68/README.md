## Build a CIP68 meme coin

Cardano's native assets are very flexible, you are in full control of:
- do you use them as NFT's, ie: only 1 quantity of 1 assetname
- do you use them as FT's, ie: 21.000.000 quantity of 1 assetname

Cardano's "old" standard to create tokens involved a Github repository, where token issuers could register their metadata (logo, url, decimals, etc).

The CIP68 standard is a new version of this, where these attributes are stored on chain. 

Keep in mind that CIP68 always works with 2 assetnames.
- the asset that is sitting in user's wallets (xxxxx quantity)
- the asset that is sitting in a separate address (under control of the token creator, often multisig). On the UXTO level of this asset we're storing these attributes in in-line datums.


