### Building an explorer

With access to the Blockfrost API you can build a user interface (in just HTML and Javascript) that will visualize the blockchain data.

For this, dive into the available Blockfrost endpoints. Below you can find 2 examples of how to query an endpoint in Javascript.

```bash
fetch('http://cardano20.ifi.uzh.ch:3000/network')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```

```bash
var response = await fetch("http://cardano20.ifi.uzh.ch:3000/network")
var data = await response.json()
console.log(data)
```

Keep in mind that UZH Blockfrost is running on HTTP, so this will not be reachable through HTTPS connections. You can run a local Python webserver fairly easily. Simply:
- create a directory
- create an index.html file
- inside the directory execute `python3 -m http.server`
- your website will be available on http://localhost:8000

