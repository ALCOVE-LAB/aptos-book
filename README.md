# aptos-book
![image](https://github.com/user-attachments/assets/7ae2d2d8-9654-47fb-b431-2bd9e065dc17)


## 使命
alcove 致力于支持富有才华的开发者，使用 Move 语言构建下一代 Web3 应用。 在 alcove ，创造更多可能。一步创新，一步成就。Make Your Move


## Move 开发环境搭建指引

### 2024残酷共学视频


## Aptos 官方 SDK & 工具链

---

### TypeScript SDK 

- 文档: https://aptos.dev/en/build/sdks/ts-sdk
- npm: https://www.npmjs.com/package/@aptos-labs/ts-sdk
- 代码库: https://github.com/aptos-labs/aptos-ts-sdk

基础示例 (发送 APT)
```javascript
  // Transfer between users
  const txn = await aptos.transaction.build.simple({
    sender: alice.accountAddress,
    data: {
      function: "0x1::coin::transfer",
      typeArguments: [APTOS_COIN],
      functionArguments: [bob.accountAddress, TRANSFER_AMOUNT],
    },
  });

  console.log("\n=== Transfer transaction ===\n");
  const committedTxn = await aptos.signAndSubmitTransaction({ signer: alice, transaction: txn });

  await aptos.waitForTransaction({ transactionHash: committedTxn.hash });
  console.log(`Committed transaction: ${committedTxn.hash}`);
```

---

### Python SDK

- 文档: https://aptos.dev/en/build/sdks/python-sdk
- pypi: https://pypi.org/project/aptos-sdk/
- 源代码: https://github.com/aptos-labs/aptos-python-sdk

```
entry_function = EntryFunction.natural(
    "0x1::aptos_account",  # Module address and name
    "transfer",            # Function name
    [],                    # Type arguments (empty for this function)
    [
        # Function arguments with their serialization type
        TransactionArgument(bob.address(), Serializer.struct),  # Recipient address
        TransactionArgument(1000, Serializer.u64),              # Amount to transfer (1000 octas)
    ],
)

chain_id = await rest_client.chain_id()
 
# Get the sender's current sequence number
account_data = await rest_client.account(alice.address())
sequence_number = int(account_data["sequence_number"])

signed_transaction = await rest_client.create_bcs_signed_transaction(
    alice,                           # Account with the private key
    TransactionPayload(entry_function),  # The payload from our transaction
    sequence_number=sequence_number  # Use the same sequence number as before
)
 
print("Transaction signed successfully")

tx_hash = await rest_client.submit_bcs_transaction(signed_transaction)
 
print(f"Transaction submitted with hash: {tx_hash}")
```

---

### Golang SDK

- 文档: https://aptos.dev/en/build/sdks/go-sdk
- 源代码: https://github.com/aptos-labs/aptos-go-sdk

---

### Rust SDK 

#### Old

老版本 Rust SDK 和 Aptos Core 结合紧密，可以直接导入 Aptos Core 进行使用

- 文档: https://aptos.dev/en/build/sdks/rust-sdk
- 源代码: https://github.com/aptos-labs/aptos-core/tree/main/sdk

#### New (Beta)

新版本 Rust SDK 依赖较少，但功能尚未完全，基础功能可用

- 源代码: https://github.com/aptos-labs/aptos-rust-sdk

---

### .Net SDK

- 文档: https://aptos.dev/en/build/sdks/dotnet-sdk
- 源代码: https://github.com/aptos-labs/aptos-dotnet-sdk

---

### Wallet Adapter

- 源代码: https://github.com/aptos-labs/aptos-wallet-adapter
- 示例: https://aptos-labs.github.io/aptos-wallet-adapter/

---

## 典型DeFi 项目案例


## 基础知识概览

### 1. Aptos 简介：
- 了解 Aptos 智能合约、数据查询接口、区块链基础设施、SDK、Indexer、Aptos Cli ... 
    [ Aptos 开始 ](https://aptos.dev/en/build/get-started)
  
<details> 
    
- [智能合约](https://aptos.dev/en/build/smart-contracts)
- [从 以太坊 到 Aptos 知识表](https://aptos.dev/en/build/get-started/ethereum-cheatsheet)
- [从 Solana 到 Aptos 知识表](https://aptos.dev/en/build/get-started/solana-cheatsheet)
- [共识机制](https://aptos.dev/en/network/blockchain/validator-nodes#consensus) 
- [账户模型](https://aptos.dev/en/network/blockchain/accounts)
- [Gas 模型](https://aptos.dev/en/network/blockchain/gas-txn-fee)
- [资源模型](https://aptos.dev/en/network/blockchain/resources)
- [交易与状态模型](https://aptos.dev/en/network/blockchain/txns-states)
- [SDK 概览](https://aptos.dev/en/build/sdks)

</details>
   
### 2. Aptos 入门开发
- 下载使用 Aptos Cli 、使用 Typescript SDK 提交交易、使用 Move 编写基本的合约代码
<details>
        
- [使用 Aptos Cli 创建你的第一个 Move 包](https://aptos.dev/en/build/smart-contracts/create-package)
- [使用 Aptos Cli 编译你的第一个 Move 包](https://aptos.dev/en/build/smart-contracts/compiling)
- [使用 Aptos Cli 测试你的第一个 Move 包](https://aptos.dev/en/build/smart-contracts/book/unit-testing)
- [使用 Aptos Cli 发布你的第一个 Move 包](https://aptos.dev/en/build/smart-contracts/deployment)
- [学习 Aptos Move 的泛型](https://aptos.dev/en/build/smart-contracts/book/generics)
- [学习 Aptos Move 的 While、For 和 Loop 循环结构](https://aptos.dev/en/build/smart-contracts/book/loops)
- [学习 Aptos Move 的 Struct 和 Resources](https://aptos.dev/en/build/smart-contracts/book/structs-and-resources)
- [学习 Aptos Move 的 Enum ](https://aptos.dev/en/build/smart-contracts/book/enums)

</details>


### Dapp开发:

#### 合约测试,React/ Nextjs 与 Aptos Wallet 的链接Ts SDK 的使用，读取链上数据、发送链上交易

### 新功能:

#### Keyless 无私钥登陆，Randomness 链上随机数Dispatchable Fungible Assets

![image](https://github.com/user-attachments/assets/b39a69c7-4f03-42f3-a57d-05e572990c98)
