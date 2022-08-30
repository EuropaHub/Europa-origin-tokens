# Europa-tokens
Approved L1 assets bridged to Europa: ```Origin``` token addresses: 
- DAI : ```0xD05C4be5f3be302d376518c9492EC0147Fa5A718```
- USDT : ```0x1c0491E3396AD6a35f061c62387a95d7218FC515```
- USDP : ```0x73d22d8a2D1f59Bf5Bcf62cA382481a2073FAF58```
- USDC : ```0x5F795bb52dAC3085f578f4877D450e2929D2F13d```
- WETH : ```coming soon``` - wrapper address
- WBTC : ```0xcb011E86DF014a46F4e3AC3F3cbB114A4EB80870```
- SKL : ```0xE0595a049d02b7674572b0d59cd4880Db60EDC50```
- RUBY : ```0x2B4e4899b53E8b7958c4591a6d02f9C0b5c50F8f```

# Dapp Chain Owners
If you would to include any of the above assets on your Skale chain, please follow the instructions below. Approval is not required from the Europa DAO to bridge Europa Origin tokens to your Skale chain. 
- 1: use private key with ```CHAIN_CONNECTOR_ROLE``` to connect skale chains using method ```connectSchain``` with input ```elated-tan-skat``` on token linker contract ```0xD2aAA00800000000000000000000000000000000``` : predeployed across all Skale chains. Please check block explorer for successful tx. 
- 2: deploy skaleERC20 token with the same ```symbol```, ```token name```, and ```decimals``` as indicated on [Europa](https://elated-tan-skat.explorer.mainnet.skalenodes.com/tokens). After deployement, you should only refer to this token contract address as the ```target_token``` address.
- 3: assign newly deployed token contract address ```MINTER_ROLE``` and ```BURNER_ROLE``` to the erc20 token manager contract ```0xD2aAA00500000000000000000000000000000000``` : predeployed across all skale chains, however please double check your erc20 token manager contract address by visiting the token linker contract on your block explorer and use method ```viewTokenManagers``` with input ```1```. Here is an example on Europa: [blockexplorer](https://elated-tan-skat.explorer.mainnet.skalenodes.com/address/0xD2aAA00800000000000000000000000000000000/read-proxy)
- 4: use method ```addERC20TokenByOwner``` with input schain ```elated-tan-skat``` , Europa ```Origin``` token address, skaleERC20 ```deployed_contract_address``` on token manager contract. Please check block explorer for successful tx.

## Transfer Origin tokens to Target chain
The final step is to transfer the Europa ```Origin``` token to your Skale chain
- rpc: ```https://mainnet.skalenodes.com/v1/elated-tan-skat``` connect to the Europa chain
- use any private key holding Europa assets.
- 1: ```Transfer to target``` : erc20 token manager contract ```0xD2aAA00500000000000000000000000000000000```with method ```transferToSchainERC20``` and input your Skale ```chain_name```, ```Origin_token_address```, and the ```amount```. The token_address must match the ```Origin_Token_Address``` on Europa.

## Transfer target tokens to Origin chain
- rpc: ```https://mainnet.skalenodes.com/v1/your-skale-chain-name``` connect to the Dapp chain
- use any private key holding Dapp Chain assets.
- 1: ```Transfer to origin``` : : erc20 token manager contract ```0xD2aAA00500000000000000000000000000000000```with method ```transferToSchainERC20``` and input ```elated-tan-skat```, ```Origin_token_address```, and the ```amount```. The token_address must match the ```Origin_Token_Address``` on Europa.


    
  
     
     
    
