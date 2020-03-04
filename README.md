# Steps to Setup the Ethereum node

1. Create an account

```
$ mkdir node
$ geth --datadir ./node account new
```

2. Create genesis file to Initialize blockchain

```
$ cd node
$ touch genesis.json
```
and copy the following content:

```
{
 "config": {
 "chainId": 1907,
 "homesteadBlock": 0,
 "eip155Block": 0,
 "eip158Block": 0,
 "eip150Block":0
 },
 "difficulty": "10",
 "gasLimit": "2100000",
 "alloc": {},
 "coinbase": "0x92737b335424c9751CdEF8D54b575b5DF1f02371"
}
```

3. Replace the coinbase key with the value of your account address, generated in step 1.

4. Run the blockchain initialization command:

```
$ geth --datadir ./node init ./node/genesis.json
```

5. Start Ethereum node, as follows:

```
$ geth --rpc --rpcaddr localhost --rpcport 6666 --rpcapi "personal,eth,web3,net" --datadir ./node console
```

6. Verify and test the blockchain:

```
> eth.getBalance(eth.coinbase)
0
```

7. Start mining:

```
> miner.start()
```

8. After few seconds stop mining with:

```
> miner.stop()
```

9. Check the balance now:

```
eth.getBalance(eth.coinbase)
370000000000000000000
```

10. Test the RPC API:

```
$ curl --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"eth_getBalance","params":["0x92737b335424c9751CdEF8D54b575b5DF1f02371","latest"]}' -H 'content-type:application/json;' http://localhost:6666 -vvvv
```

Replace 0x92737b335424c9751CdEF8D54b575b5DF1f02371 your account address, generated in step 1. Result is in hash, use this tool to check the decimal value - https://codebeautify.org/hex-decimal-converter


References:

1. https://medium.com/@przemekthomann/setup-ethereum-development-environment-in-5-minutes-51336c013fdb
