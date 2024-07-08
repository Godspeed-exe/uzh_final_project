## Transaction Chaining

The initial Python script uses PyCardano's `builder.add_input_address(main_address)` function to:
1. query the Blockfrost API for all available inputs
2. select the inputs needed to satisfy the outputs which are requested

This is easy and works for one shot transactions for most of the time. But if you are looking to "rapid fire" transactions you might want to do transaction chaining. 

What happens with the Blockfrost approach?
- Query the inputs
- Build the transaction
- Submit the transaction
- re-query the inputs

This last step will return the same inputs, since the transaction has not settled on the network yet and your following transaction will fail. The error will probably contain "BadInputs" - this means you are trying to spend something that does not belong to you or that does not exist (anymore).

The trick for transaction chaining is, since you know the transaction_hash of the transaction you just created, you know the index (of the change, coming back to your wallet). So you can use this knowledge to construct the next inputs yourself.

You can work around this by:
- Query the inputs
- Cache them
- Build your transaction processing off this cache 
- Remove used inputs from the cache
- Add newly created inputs to the cache
- Repeat
- Only query the inputs again if you get a "BadInputs" error.

With creating this type of transactions, you have the risk of running into a rollback on-chain. Foresee this event in your backend process by:
- transactions that need processing get status 0 , transaction_dt is null 
- transactions that have been processed get status 1 , transaction_dt is stored 
- transactions that have been processed and the transaction_dt is longer then 5 minutes ago: check if the transaction_id still exists. 
    - if YES: set status 2
    - if NO: set status to 0 (this needs to be reprocessed)