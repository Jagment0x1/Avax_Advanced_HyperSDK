# Metacrafters Avalanche Module 2: Avalanche HyperSdk 'tokenvm' 

The HyperSDK Chain is a high-performance, customizable blockchain built using Avalanche’s HyperSDK framework. It leverages Avalanche's subnets and modular infrastructure to enable the rapid development of decentralized applications (dApps) with native support for smart contracts, digital assets, and tokenized economies.

The chain is designed to cater to various use cases, including decentralized finance (DeFi), gaming, and marketplaces. Through an efficient set of commands such as mint-asset, create-asset, create-order, fill-order, and close-order, users can seamlessly manage assets and trade on-chain, while benefiting from the scalability and security provided by the Avalanche consensus protocol.

HyperSDK is ideal for developers seeking a balance between flexibility and performance, with the ability to build custom features and integrate with Ethereum Virtual Machine (EVM) ecosystems like Metamask, enabling seamless interaction with dApps, decentralized exchanges, and wallets.

<img src="https://github.com/Metacrafters/tokenvm/raw/main/assets/hypersdk.png">

### Features

**Mint Asset:** Issue new tokens on the chain.</br>
**Create Asset:** Define and deploy a new asset class.</br>
**Create Order:** List assets for sale or trade on the marketplace.</br>
**Fill Order:** Purchase or trade an asset from an open order.</br>
**Close Order:** Close an active order on the marketplace.</br>

# Steps To Reproduce 

## Step 1: Create Your Asset

To create a new asset, use the following command from the specified directory:

```bash
./build/token-cli action create-asset
```

Once complete, you should see output similar to this:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
metadata (can be changed later): MarioCoin
continue (y/n): y
✅ txID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
```

- **`txID`** is the assetID of your new asset.
- The **loaded address** is the default private key, which is used for all interactions with the blockchain.

## Step 2: Mint Your Asset

Now that you've created an asset, you can mint tokens for it using this command:

```bash
./build/token-cli action mint-asset
```

Example output:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
assetID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
metadata: MarioCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 10000
continue (y/n): y
✅ txID: X1E5CVFgFFgniFyWcj5wweGg66TyzjK2bMWWTzFwJcwFYkF72
```

## Step 3: View Your Balance

To verify that minting was successful, you can check your balance with this command:

```bash
./build/token-cli key balance
```

Sample output:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
assetID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
metadata: MarioCoin supply: 10000 warp: false
balance: 10000 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
```

## Step 4: Create an Order

You can now place an order to trade your new asset on-chain using this command:

```bash
./build/token-cli action create-order
```

Sample output:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
in assetID (use TKN for native token): TKN
✔ in tick: 1█
out assetID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
out tick: 10
supply (must be multiple of out tick): 100
continue (y/n): y
✅ txID: 2TdeT2ZsQtJhbWJuhLZ3eexuCY4UP6W7q5ZiAHMYtVfSSp1ids
```

- **`in tick`** is how much of the incoming asset is required to obtain the outgoing asset.
- **`txID`** is the orderID for your new order.

## Step 5: Fill Part of the Order

To fill an order and exchange assets, run the following command:

```bash
./build/token-cli action fill-order
```

Example output:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
in assetID: TKN
balance: 997.999993843 TKN
available orders: 1
Rate(in/out): 100000000.0000 InTick: 1 TKN OutTick: 10
select order: 0
value (must be multiple of in tick): 2
continue (y/n): y
✅ txID: uw9YrZcs4QQTEBSR3guVnzQTFyKKm5QFGVTvuGyntSTrx3aGm
```

## Step 6: Close an Order

To close an order and remove it from the marketplace, run this command:

```bash
./build/token-cli action close-order
```

Example output:

```
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
orderID: 2TdeT2ZsQtJhbWJuhLZ3eexuCY4UP6W7q5ZiAHMYtVfSSp1ids
continue (y/n): y
✅ txID: poGnxYiLZAruurNjugTPfN1JjwSZzGZdZnBEezp5HB98PhKcn
```

--- 
