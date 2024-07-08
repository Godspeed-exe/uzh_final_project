## Wallet Connect

By default all Cardano wallets register themselves in your browser under the `window.cardano` namespace.

### Scanning installed wallets
You can loop over all installed wallets, each element (that is an actual wallet - since it also has other elements) in the namespace has a .enable() function.

**Javascript**

    var cardano = window.cardano

    if(cardano !== undefined){
        $("#installed_wallets").empty()
        
        Object.getOwnPropertyNames(cardano).forEach(function(name) {
            if(eval("window.cardano."+name+".enable") !== undefined){
                var icon = eval("window.cardano."+name+".icon")
                $("#installed_wallets").append(`<a class="dropdown-item" href="#" onClick='start_delegation("${name}")'><img style="height:20px" class="img-fluid mr-3" src="${icon}"> ${name}</a>`)
            }
        });
    }



### Talking to Nami

You can talk to Nami through Javascript or your browser console like:

    var wallet = await window.cardano.nami.enable()

If your website / URL is not yet whitelisted on Nami this will show a popup to allow / reject access.
With this access you have access to several endpoints:

- wallet.getUtxos()
- wallet.getBalance()

You can find a full set of available endpoints on [Nami's Github](https://github.com/input-output-hk/nami?tab=readme-ov-file#methods).

### Tips
- Take into account the encoding of these API's, this is mostly in CBOR or HEX.


