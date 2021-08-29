# Task 11) Use A Tron Wallet To Execute A Smart Contract Call

Screenshot of the accounts I created:

![](https://raw.githubusercontent.com/Venoox/ckb-gitcoin-tasks/main/task01/ckb-cli-account-list.png)

Layer 1 testnet address explorer: https://explorer.nervos.org/aggron/address/ckt1qyqv6jhgx5jrwhyd8tueqem3ed29gu3zrwzsayurt3

A screenshot of the console output immediately after you have successfully submitted a CKByte deposit to your Tron account on Layer 2:

![Console output](https://user-images.githubusercontent.com/21956707/131251510-45fc5423-e919-4ec3-b199-ddcaf70b20e9.png)

A screenshot of the console output immediately after you have successfully issued a smart contract calls on Layer 2:

![Console output](https://user-images.githubusercontent.com/21956707/131251934-115c5886-e737-4ddc-b0e8-7ec962926788.png)

Transaction hash of the contract write call: `0xa0eadd6d7a91c56a0f2f408306afab4a8919aa7ca567216eadc4fb40cfc89dec`

Contract address: `0x050a276FA74B6Be21170990b2f757D37ddA3e353`

ABI:
```
[
    {
      "inputs": [],
      "stateMutability": "payable",
      "type": "constructor"
    },
    {
      "inputs": [
        {
          "internalType": "uint256",
          "name": "x",
          "type": "uint256"
        }
      ],
      "name": "set",
      "outputs": [],
      "stateMutability": "payable",
      "type": "function"
    },
    {
      "inputs": [],
      "name": "get",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "stateMutability": "view",
      "type": "function"
    }
]
```

Tron address: `TDbADMFZVkAamYzQ76vVGjVF8dfFhEqjH1`
