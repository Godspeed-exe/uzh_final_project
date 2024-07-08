## About The Repo

In this repo you can find some ideas for your final project and also some resources which might be useful to complete the project. Of course, you are free to use your own creativity to come up with variations on these examples.

In case you have any questions feel free to reach out!

## Use Blockfrost API 

UZH's Cardano network has it's own Blockfrost instance which you can use to query blockchain data. There are a few options to explore this:

### Using Postman
- Install Postman (https://www.postman.com/downloads/)
- Import the custom Postman configuration from [here](blockfrost_api/uzh_blockfrost.json) for the UZH network - in order to import you need to create a Postman account.
- You'll have all the available API calls available in Postman.

### Using your browser
- If you take a look at the [Blockfrost API documentation](https://blockfrost.dev/api/blockfrost-io-api-documentation) you can find an overview of all the API calls.
- The base URL for UZH Blockfrost is http://130.60.144.75:3000


## Submitting Transactions
UZH is running a local Submit API. You can submit created transactions to http://cardano20.ifi.uzh.ch:8090/api/submit/tx

**Python**
```bash
        headers = {'Content-Type': 'application/cbor'}
        response = requests.post("http://cardano20.ifi.uzh.ch:8090/api/submit/tx", data=signed_tx.to_cbor(), headers=headers)
```


## Overall Developer tools
You can find a large repository of Cardano developer tools on https://developers.cardano.org/tools