# aptos-book
![image](https://github.com/user-attachments/assets/7ae2d2d8-9654-47fb-b431-2bd9e065dc17)


## 使命
alcove 致力于支持富有才华的开发者，使用 Move 语言构建下一代 Web3 应用。 在 alcove ，创造更多可能。一步创新，一步成就。Make Your Move


## Move 开发环境搭建指引

### 2024残酷共学视频


## Aptos 官方 SDK & 工具链

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

<details> 

<summary>点击展开</summary>
    
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

<summary>点击展开</summary>

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

## 一个快速起项目的方式

### 1.配置你的aptos

安装aptos CLI

https://aptos.dev/en/build/cli

### 2.撰写MOVE合约

参考文档：https://aptos.dev/en/build/smart-contracts/deployment

撰写步骤

1.打开终端`cd 你想把项目放置的文件夹`

2.执行命令`aptos move init --name <PROJECT_NAME>`

3.找到生成的文件夹中的`move.toml`文件，填入下面的内容，my_address名字为在`source`文件夹中创建的move合约名，也是move合约中的`object`名字

```rust
[addresses]
my_address = "_"
```

4.编写MOVE合约

5.执行命令`aptos init` 配置私钥地址和网络，该地址需要有一定的aptos测试币用于支付gas费

6.执行命令`aptos move compile --named-addresses <named_address>=<your_address>`编译move合约

7.执行命令`aptos move deploy-object --address-name my_address`部署智能合约

### 3.撰写前端项目

前端调用合约函数时，一般有两种方式：

#### ✅ 方式一：自动生成 ABI 代码后调用（推荐）

- 利用工具将 Move 合约编译成 ABI（Application Binary Interface）文件
- 前端通过 SDK 调用 ABI 暴露的方法
- 参考：https://github.com/aptos-labs/aptogotchi-random-mint 中front/gen_abi.sh文件
- **优点**：类型安全、调试友好、前后端协作清晰
- **适合对象**：希望构建标准化、长期维护的项目团队

#### ✅ 方式二：手动书写模块调用代码（灵活）

- 直接使用类似 wallet.module.method() 的写法调用链上函数
- 可参考https://github.com/aptos-labs/move-by-examples/tree/main/fungible-asset-launchpad/aptos和https://github.com/aptos-labs/move-by-examples/tree/main/nft-marketplace
- **优点**：对 Move 熟悉的人更灵活，可快速验证想法
- **适合对象**：熟悉合约结构，喜欢动手调试和定制化逻辑的开发者

### 4. 前后端连接路径

完整的 DApp 项目包含以下几个步骤：

1. ✍️ **编写 Move 合约**
2. 🔧 **在链上部署**
3. 🖥️ **前端集成，调用合约函数**
4. 🧪 **完成页面交互逻辑**
5. 🚀 **部署上线或提交黑客松作品**
