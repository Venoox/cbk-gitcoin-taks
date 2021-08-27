# Task 7) Port An Existing Ethereum DApp To Polyjuice

For this task I used my simple decentralized voting app that I wrote a while ago with Truffle and React. It features registered voting so only addresses set on contract deployment can vote, there's a start and end time, question as in string, and multiple answers.

The contracts are already deployed and if you want to test you can only run React app and it should load current contracts on godwoken testnet.
If you wanna deploy contracts yourself you need add mnemonic to `app/src/config.js` and run `truffle migrate --network godwoken` and test with React.
I had some issues with nervos-godwoken-integration so I followed danielkmak's advice and ejected React app and added 3 Babel plugins: `@babel/plugin-proposal-class-properties`, `@babel/plugin-proposal-nullish-coalescing-operator` and `@babel/plugin-syntax-bigint`.
After that I couldn't interact with the contract and didn't receive any errors and after some conversation with danielkmak on Discord server, I found out that godwoken testnet has issues with reverting contract methods and my issue was that I was storing eth addresses instead of polyjuice addresses in the contract. After I fixed that it wasn't better so I thought something is wrong with `block.timestamp` and after disabling the part of contract checking timestamp, everything worked!
I also disabled the part checking if you are a registered voter so you can test this app without deploying the contract yourself.

Original dApp: https://github.com/Venoox/decentralized-voting-app/tree/main
Ported dApp: https://github.com/Venoox/decentralized-voting-app/tree/godwoken

Video proof:

https://user-images.githubusercontent.com/21956707/131161119-38176a93-f60c-4894-9a75-788a1dd58b47.mp4

Contract `Migrations`:
- Transaction hash: 0x33b1e4a4284b964ea9f7c00e38a211e5ad7a17fbc828fe4741fd68b4f0850478
- Deployed contract address: 0xd7136F7bc10270A21c18B19d9ba557d89F5BF116
```
[
    {
      "inputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "last_completed_migration",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "owner",
      "outputs": [
        {
          "internalType": "address",
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "completed",
          "type": "uint256"
        }
      ],
      "name": "setCompleted",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    }
  ]
```

Contract `Voting`:
- Transaction hash: 0x10c1fb2766e14d0c122e4292e407655d2b60d52b787a5d42490520b9041c74e6
- Deployed contract address: 0x83bf558F541e2EA78A9F0a72700614568a74fC7E

```
[
    {
      "inputs": [
        {
          "internalType": "string",
          "name": "_question",
          "type": "string"
        },
        {
          "internalType": "string[]",
          "name": "_answers",
          "type": "string[]"
        },
        {
          "internalType": "address[]",
          "name": "_voters",
          "type": "address[]"
        },
        {
          "internalType": "uint256",
          "name": "_startTimestamp",
          "type": "uint256"
        },
        {
          "internalType": "uint256",
          "name": "_endTimestamp",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "name": "answers",
      "outputs": [
        {
          "internalType": "string",
          "name": "answer",
          "type": "string"
        },
        {
          "internalType": "uint256",
          "name": "count",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "endTimestamp",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "question",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "startTimestamp",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "votersCount",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "index",
          "type": "uint256"
        }
      ],
      "name": "vote",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "getAnswersCount",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "getAllAnswers",
      "outputs": [
        {
          "components": [
            {
              "internalType": "string",
              "name": "answer",
              "type": "string"
            },
            {
              "internalType": "uint256",
              "name": "count",
              "type": "uint256"
            }
          ],
          "internalType": "struct Voting.Answer[]",
          "name": "",
          "type": "tuple[]"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "getVotedCount",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "count",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "getMostVoted",
      "outputs": [
        {
          "components": [
            {
              "internalType": "string",
              "name": "answer",
              "type": "string"
            },
            {
              "internalType": "uint256",
              "name": "count",
              "type": "uint256"
            }
          ],
          "internalType": "struct Voting.Answer",
          "name": "",
          "type": "tuple"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    }
  ]
```


