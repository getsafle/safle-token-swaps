# **Inblox Token Swaps**

Inblox Token Swap SDK
> Disclaimer - This is WIP, and release in beta.


## **Token Swap**

> Initialising

Initialise the constructor using,

`const tokenSwapWidget = new inbloxTokenSwaps.Widget({rpcURL, env, etherscanSecret});` 

* `env` - API environments (eg. dev, test) 
* `etherscanSecret` - Etherscan secret key
* `web3URL` - Web3 RPC provider URL

Serve the widget on your application by calling the `initTokenSwap` method

`tokenSwapWidget.initTokenSwap();`

Widget Event Listeners

> Successful widget initialization

`tokenSwapWidget.on(keylessWidget.EVENTS.TOKEN_SWAP_WIDGET_INITIALISED, (data) => {
	console.log(data)
});`

> Widget close

`tokenSwapWidget.on(keylessWidget.EVENTS.TOKEN_SWAP_WIDGET_CLOSED, (data) => {
	console.log(data)
});`


> Transaction success

`tokenSwapWidget.on(keylessWidget.EVENTS.TOKEN_SWAP_TRANSACTION_SUCCESSFUL, (data) => {
	console.log(data)
});`


> Sign and send Transaction Failure

`tokenSwapWidget.on(keylessWidget.EVENTS.TOKEN_SWAP_TRANSACTION_FAILED, (data) => {
	console.log(data)
});`


## **SDK methods**


> Initialising

Initialise the constructor using,

`const swap = new TokenSwap('rpcUrl', 'etherscanSecret');`


> Swap Tokens

This method can be used to swap a given pair of tokens.

`const tokenSwap= await swap.swapTokens({ srcTokenAddress, dstTokenAddress, srcDecimal, srcQty, privateKey, wallet, userAddress});`

* `srcTokenAddress` - source token contract address
* `dstTokenAddress` - destination token contract address
* `userAddress` - user's public address
* `srcDecimal` - decimal of source tokens,
* `srcQty` - source token quantity,
* `wallet` - wallet type, (valid values: handlename, keyStore, privateKey, metamask)
* `privateKey` - user's private key (only req. of wallet type is privateKey/keystore)


> Get rates

This method can be used to get expected and slippage rates.

`const rates= await swap.getRates(srcTokenAddress, dstTokenAddress, srcQtyWei);`

* `srcTokenAddress` - source token contract address
* `dstTokenAddress` - destination token contract address
* `srcQtyWei` - source token quantity in wei,

> Convert eth to wei

This method can be used to convert amount in eth to wei

`const qtyInEth= await swap.convertEthToWei(srcQty);`

`srcQty` - source token quantity in eth


> Get wallet balance

This method can be used to get user's ether balance

`const balance = await swap.getWalletBalance(walletAddress);`

`walletAddress` - user's public address


> Get slippage percentage

This method can be used get slippage percentage

`const slippage= await swap.getSlippage(srcTokenAddress, dstTokenAddress, srcQty);`

* `srcTokenAddress` - source token contract address
* `dstTokenAddress` - destination token contract address
* `srcQty` - source token quantity in eth



> Get Token Balance

This method can be used to  get balance of a particular token.

`const tokenBalance= await swap.getTokenBalance(srcTokenAddress, userAddress);`

* `srcTokenAddress` - source token contract address
* `userAddress` - public address of user


> Get exchange rates

This method can be used to get exchange rate.

`const rate= await swap.getExchangeRates(srcTokenAddress, dstTokenAddress, srcDecimal, dstDecimal)`

* `srcTokenAddress` - source token contract address
* `dstTokenAddress` - destination token contract address
* `srcDecimals` - decimals of source token
* `dstDecimals` - decimals of destination token


> Sign and send transaction

This method can be used to sign and send a transaction

`const transaction= await swap.signAndSendTransaction({ wallet, rawTx });`

* `wallet` - wallet type, (valid values: handlename, keyStore, privateKey, metamask)
* `rawTx` - raw transaction


> Get tokens list

This method can be used to get list of supported tokens.

`const tokenList= await swaps.getTokensList()`


> Get gas limit

This method can be used to get gas limit for swap transaction

`const gasLimit= await swaps.getGasLimit(srcTokenAddress, dstTokenAddress, amount);`

* `srcTokenAddress` - source token contract address
* `dstTokenAddress` - destination token contract address
* `amount` - source token amount


## **Helper methods**

> Get destination quantity

This method can be used to get the destination quantity.

`const destQty= await inbloxTokenSwaps.getDstQty(srcQty, srcDecimals, dstDecimals, rate);`

* `srcQty` - number of source tokens to be swapped
* `srcDecimals` - decimals of source token
* `dstDecimals` - decimals of source token
* `rate` - exchange rate


> Get source quantity

This method can be used to get the source quantity.

`srcQty= await inbloxTokenSwaps.getSrcQty(dstQty, srcDecimals, dstDecimals, rate);`

* `dstQty` - number of source tokens to be swapped
* `srcDecimals` - decimals of source token
* `dstDecimals` - decimals of source token
* `rate` - exchange rate


> Get wallet

This method can be used to get user's wallet details.

`const wallet= await inbloxTokenSwaps.getWallet({ wallet, infuraKey, keystoreJson, passphrase, privateKey});`

* `wallet` - wallet type, (valid values: keyStore, privateKey, metamask)
* `infuraKey` - infura key (only req. if wallet type is privateKey),
* `keystoreJson` - user's wallet encrypted JSON(only req. if wallet type is keyStore),
* `passphrase` - password to decrypt keystore json(only req. if wallet type is keyStore)
* `privateKey` - user's private key(only req. if wallet type is privateKey),



## **WIP**

Want to contribute, we would ❤️ that!

We are a Global 🌏🌍🌎 team! 💪

Write to [dev@inblox.me](mailto:dev@inblox.me), or follow us on twitter, [https://twitter.com/inblox_me](https://twitter.com/inblox_me)
