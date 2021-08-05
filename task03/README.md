# Task 3) Issue A Smart Contract Call To The Deployed Smart Contract

This task involved setting up parameters in index.js and running the script which reads and writes to the contract.

Transaction hash: `0x4c743e613da9ca7811908527b9cda1f1f2d56d287ffca5d91058ca9cb13f6336`

Contract address: `0x050a276FA74B6Be21170990b2f757D37ddA3e353`

ABI:
```json
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

Screenshot of running the script:

![Console output](https://raw.githubusercontent.com/Venoox/ckb-gitcoin-tasks/main/task03/contract_read_and_write_output.png)
