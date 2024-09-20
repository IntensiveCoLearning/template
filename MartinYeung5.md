---
timezone: Asia/Shanghai
---

# MartinYeung5

1. 自我介绍
* Martin Yeung, 來自中國香港，計算機科學+電商專業，香港城市大學理學碩士畢業，專注於區塊鏈技術研究和應用。

2. 你认为你会完成本次残酷学习吗？
* 會的。

## Notes

<!-- Content_START -->

### 2024.09.07




Aptos是基於MOVE語言的一個公鏈，利用MOVE可以構建一個更安全的智能合約，特別是用於數字資產領域，會突顥出其價值，當然也需要看是在怎樣的應用場景。 
針對MOVE智能合約的開發，有不同的知識點需要學習，需要理解不同代碼的原理及應用方式。
要建立完整的Aptos項目，在完成MOVE智能合約的開發後，
需要設計frontend及與智能合約的進行交互，而我最近在學習與智能合約的交互，
透過web3電子錢包讓用戶可以與平台/智能合約互動。


今天想分享一下我對useWallet的學習和了解，
Frontend交互部分，我用了@aptos-labs/wallet-adapter-react，透過它使用到useWallet，然後從useWallet獲得需要用到的功能，如下:

```
const {
    connected,
    account,
    network,
    signAndSubmitTransaction,
    signMessageAndVerify,
    signMessage,
    signTransaction,
} = useWallet();
```

使用useWallet，可以讓用戶進行一些簽名及提交交易的動作。
* 第一個例子(signMessage)是讓用戶對一項訊息進行簽名:

```
  const onSignMessage = async () => {
    const payload = {
      message: "Hello，我是Martin Yeung，對Aptos相當感興趣。",
      nonce: Math.random().toString(16),
    };

    //簽名後的回應訊息為response，可以留意到const response的類型是"SignMessageResponse"，
    //這個就是通過signMessage()所獲得到訊息類型
    
    const response = await signMessage(payload);
    
    //顯示response的訊息內容，以便做debug
    //而且可以讓用戶知道自己最終是否成功完成簽名
    //當中的await就是等待signMessage的回應，如果signMessage完成就能返會一些訊息。
    //如果沒有await的話，系統就不會一直等待signMessage的回應，所以會出現跳過signMessage回應的情況
    //有機會出現的情況就是signMessage失敗，但完成onSignMessage這功能。
    
    console.log(response);
  };
```

用戶執行以上功能的流程:
1. 在frontend頁面，當用戶觸發到onSignMessage功能，就會執行到以上的動作
2. 用戶的web3電子錢包會彈出
3. 在錢包上會顯示"Hello，我是Martin Yeung，對Aptos相當感興趣"
4. 及要求用戶對這訊息進行簽名，
因為這要確保用戶是能清楚知道自己是對什麼東西進行簽名確認，
5. 如果用戶確認沒問題，就可以在錢包上點擊"Sign"進行簽名的動作
6. 用戶等待簽名完成的回應 (這個可以在Frontend設計一個顯示回應的訊息，讓用戶知道最終結果)


* 第二個例子(signAndSubmitTransaction)是讓用戶對一項交易進行簽名及提出交易動作:
假設用戶需要轉帳APTOS到某個指定錢包，需要用戶進行簽名及交易。

```
  const APTOS_COIN = "0x1::aptos_coin::AptosCoin";
  const onSignAndSubmitTransaction = async () => {
    if (!account) return;
    const transaction: InputTransactionData = {
      data: {
        function: "0x1::coin::transfer",
        typeArguments: [APTOS_COIN],
        functionArguments: [account.address, 1], // 1 is in Octas
      },
    };
    try {

      //簽名後的回應訊息為response，可以留意到const response的類型是"any" 
      const response = await signAndSubmitTransaction(transaction);
      await aptosClient(network).waitForTransaction({
        transactionHash: response.hash,
      });
      console.log(response);

    } catch (error) {
      console.error(error);
    }
  };
```

在上面第二個的例子，可以留意到response的類型是any，跟第一個例子不同，因為它們所返回的訊息是有所不同，
在第二個例子返回的訊息是一個已完成簽名及已完成交易動作的紀錄。

第三個例子(signMessageAndVerify)是讓用戶對一項訊息進行簽名及進行確認:

```
  //
  const onSignMessageAndVerify = async () => {
    const payload = {
      message: "Hello，我是Martin Yeung，對Aptos相當感興趣。",
      nonce: Math.random().toString(16),
    };

    //簽名後的回應訊息為response，可以留意到const response的類型是"boolean"
    const response = await signMessageAndVerify(payload);
    console.log(response);
  };
```

在上面第三個的例子，可以留意到response的類型是boolean，跟第一、二個例子不同，
因為這個例子的目的是要用戶進行簽名及進行確認，所以返回的訊息只有true或false。
當然在第一個例子也可以通過做一些額外判斷(需要進一步編寫代碼)而獲得true或false，
但這例子就簡單直接，所以可以根據自己的需求而使用合適的功能。

### 2024.09.08


繼續昨天對useWallet的學習和了解，
第四個例子(signTransaction)是讓用戶進行一項交易動作:

```
  // Legacy typescript sdk support
  const onSignTransaction = async () => {
    try {
      const payload = {
        type: "entry_function_payload",
        function: "0x1::coin::transfer",
        type_arguments: ["0x1::aptos_coin::AptosCoin"],
        arguments: [account?.address, 1], // 1 is in Octas
      };

      // 交易完成後的回應為response，可以留意到const response的類型是"AccountAuthenticator"。
      const response = await signTransaction(payload);
      console.log(response);
    } catch (error) {
      console.error(error);
    }
  };
```

可以看到signTransaction中的參數是payload，它的type是"entry_function_payload"，
當動作完成後返回的數據類型是"AccountAuthenticator"。


第五個例子(signTransaction)也是讓用戶進行一項交易動作:

```
  const onSignTransactionV2 = async () => {
    if (!account) return;

    try {
      const transactionToSign = await aptosClient(
        network,
      ).transaction.build.simple({
        sender: account.address,
        data: {
          function: "0x1::coin::transfer",
          typeArguments: [APTOS_COIN],
          functionArguments: [account.address, 1], // 1 is in Octas
        },
      });
      
      // 交易完成後的回應為response，可以留意到const response的類型是"AccountAuthenticator"。
      const response = await signTransaction(transactionToSign);
      bobSenderAuthenticator = response;
      console.log(response);
    } catch (error) {
      console.error(error);
    }
  }
```

在這個例子中，signTransaction的參數是transactionToSign，而transactionToSign是通過"transaction.build.simple"獲得。跟第四個例子相比，主要是signTransaction的參數不同，不過最終的結果是相同的，所得出的類型也是一樣。

### 2024.09.09

* 創建智能合約
創建智能合約，在Aptos只需通過一句簡單命令即可完成。
```
aptos move init --name my_todo_list
```
當執行完成之後，就可會出現以下訊息:
```
{
  "Result": "Success"
}
```

在當下目錄會出現4個文件，分別是3個文件夾及一個Move.toml文件。

文件夾有scripts, sourcesm, tests，而我們在執行命令所輸入到的 -- name my-todo_list 
就會出現在Move.tome文件內。

* 安全性
針對安全性，Aptos有以下4個優勢:
1. Formal Verification	
* Aptos framework is fully specified and formally verified with the Move Prover. This includes the core contracts involving governance, NFTs, and Tokens.
2. Gas Coverage	
* Move VM has 100% gas coverage. Gas is charged based upon actual usage in the system (CPU, memory, storage, I/O). In other words, no gas exploits.
3. Security Redundancy	
* Security redundancy provided by runtime safety checks.
4. Permission Controls	
* Permission controls can flexibly be built at various levels. For example, token level permission controls exist by default to enable RWA tokenization.

### 2024.09.10

* Authenticator
在aptos, 未簽名的交易會被視為"RawTransaction"。
它們會包含所有有關在Aptos上執行的動作的訊息，但就沒有包括到合適的有效簽名或Authenticator。
在Aptos區塊鏈上，所有數據都會被加密為BCS(Binary Canonical Serialization)。
而Aptos也會支持多種簽名方式，會以Ed25519作為預設的選擇，大家可以根據自己的項目情況而作出更改。
Authenticator在執行交易的簽名過程中，會給Aptos區塊鏈櫂限來執行用戶的交易動作。
所以把Authenticator理解為收集用戶簽名權限的地方，然後再交給Aptos區塊鏈去執行最終的動作。


### 2024.09.11


* 怎樣使到RawTransaction 成為一個已簽名的交易
1. 首先用戶在頁面提供交易動作後，在經過區塊鏈最終確認前，會先被加密成為BCS，
2. 然後通過Serialization對訊息進行簽名，在這過程中，需要獲得用戶的private key，再利用用戶的private key
來生成一個有效的交易簽名。在這一步會產生一個RawTransaction的簽名，但仍未進行交易的。
3. 之後會經過Authenticator進行下一步動作，Authenticator會獲取用戶的public key和較早前獲到的RawTransaction的簽名。
4. 當Authenticator成功收集到兩項資料就會讓Aptos進行最後的交易簽名的動作。

### 2024.09.12


建立一個已簽名的文易
1. Raw Transaction
首先 raw transaction是由以下幾個部分組成的:
* 發送者的地址(Address)
* 一組序號(unit64): 這組數字是針對當下的交易，而它也是必須與儲存在發送者戶口中的序號相符。
* Payload：Aptos區塊鏈的指令，包括發佈模組、執行腳本函數或執行腳本有效負載。
* max_gas_amount (uint64): 此交易花費的最大總gas fee。帳戶必須擁有大過此gas fee的通證，
否則交易將在驗證過程中被丟棄。


### 2024.09.13
針對建立一個已簽名的交易，可以透過整個流程進作一步了解。
當中有幾個重點部分/術語可以深入認識。
* Raw Transaction
* BCS
* Signing message
* Signature
* Signed transaction
* Multisignature transactions


### 2024.09.14
建立一個已簽名的交易，以下是整個流程:
* 第一步: Creating a RawTransaction
這例子是假設交易具有腳本函數的負載。
```
interface AccountAddress {
  // 32-byte array
  address: Uint8Array;
}

interface ModuleId {
  address: AccountAddress;
  name: string;
}

interface ScriptFunction {
  module: ModuleId;
  function: string;
  ty_args: string[];
  args: Uint8Array[];
}

interface RawTransaction {
  sender: AccountAddress;
  sequence_number: number;
  payload: ScriptFunction;
  max_gas_amount: number;
  gas_unit_price: number;
  expiration_timestamp_secs: number;
  chain_id: number;
}

function createRawTransaction(): RawTransaction {
  const payload: ScriptFunction = {
    module: {
      address: hexToAccountAddress("0x01"),
      name: "AptosCoin",
    },
    function: "transfer",
    ty_args: [],
    args: [
      BCS.serialize(hexToAccountAddress("0x02")), // receipient of the transfer
      BCS.serialize_uint64(2), // amount to transfer
    ],
  };

  return {
    sender: hexToAccountAddress("0x01"),
    sequence_number: 1n,
    max_gas_amount: 2000n,
    gas_unit_price: 1n,
    // Unix timestamp, in seconds + 10 minutes
    expiration_timestamp_secs: Math.floor(Date.now() / 1000) + 600,
    payload: payload,
    chain_id: 3,
  };
}
```

* 第二步: Creating a RawTransaction
步驟 2. 建立簽名訊息及進行簽名
1. 利用字串 APTOS::RawTransaction 的 SHA3_256 雜湊位元組產生前綴 (prefix_bytes)。
2. BCS 序列化 RawTransaction 的位元組。
3. 連接前綴和 BCS 位元組。
4. 使用用戶私鑰對位元組進行簽署。


### 2024.09.15
* 交易的生命周期
為了更深入了解 Aptos 交易的生命週期（從操作角度），會追蹤交易的整個過程。
從提交到 Aptos fullnode，到提交到 Aptos 區塊鏈。
接下來會將重點放在 Aptos 節點的邏輯元件，看看交易如何與這些元件互動。

* 前設:
1. Alice 和 Bob 是兩個用戶，每個人在 Aptos 區塊鏈上都有一個帳戶。
2. Alice的帳戶有110個Aptos幣。
3. Alice 正在向 Bob 發送 10 個 Aptos 幣。
4. Alice帳戶目前的序號是5（這表示Alice帳戶已經發送了5筆交易）。
5. 網路上共有 100 個驗證節點 — 由 V1 到 V100。
6. Aptos 用戶端將 Alice 的交易提交到 Aptos fullnode上的 REST 服務。
fullnode將此交易轉送給驗證器fullnode，驗證器fullnode將其轉送給驗證器 V1。
7. 驗證者 V1 是本輪的提議者/領導者。

* 客戶提交交易:
Aptos 用戶端建立一個原始交易（稱為 T5），
將 10 個 Aptos 幣從 Alice 的帳戶轉移到 Bob 的帳戶。 
Aptos 用戶端使用 Alice 的私鑰對交易進行簽署。已簽署的交易T5包括以下：

* 原始交易
* Alice的公鑰
* Alice的簽名

原始交易包括以下欄位：
1. 帳戶地址: Alice的帳戶地址
2. Move模組: 包含 Alice 執行的操作的模組（或程式）。當中有：
* Move字節碼的點對點交易腳本
* 腳本輸入的清單（包含 Bob 的帳戶地址和 Aptos 幣的支付金額）。
3. 最大Gas的數量: 
Alice 願意為此交易支付的最大天然氣量。 Gas 是支付計算和儲存費用的一種方式。\
Gas的單位是計算的抽象測量。
4. Gas 價格: 
Alice 願意為執行交易每單位 Gas 支付的金額（以 Aptos 幣為單位）。
5. 到期時間: 
交易的到期時間。
6. 序號: 
帳戶的序號（例子為 5）表示已從該帳戶在鏈上提交和落實的交易數量。
在例子中，Alice 的帳戶已提交 5 筆交易，其中包括 T5。
注意：序號為5的交易只有在帳號序號為5的情況下才能在鏈上提交。
7. Chain ID: 
區分 Aptos 網路部署的識別碼（以防止跨網路攻擊）。

### 2024.09.16
#### 交易的生命周期
![alt text](https://github.com/MartinYeung5/intensive-colearning-aptos/blob/main/20240916_lifecycle_of_transaction.svg?raw=true)

交易的生命週期分為五個階段：
1. 接受：接受交易
2. 分享：與其他驗證節點分享交易數據
3. 提議：向區塊提出提議
4. 執行與共識：執行區塊汞達成共識機制
5. 提交：向區塊提出提交

### 2024.09.17
#### 驗證節點介紹
Aptos 節點是 Aptos 生態系統中的一個實體，目的是用於追蹤 Aptos 區塊鏈的狀態。
客戶端可以透過 Aptos 節點與區塊鏈互動。
Aptos 有兩種類的節點: 分別是驗證者節點及完整節點。

當交易提交到Aptos區塊鏈時，驗證節點運行分希式的共識協議，執行交易，
並將交易和執行的交易結果儲存在區塊鏈上。驗證者節點會決定將哪些交易新增到區塊鏈及以順序形式執行。

Aptos 區塊鏈使用拜占庭容錯（Byzantine Fault Tolerance, BFT）共識協議讓驗證者節點就最終交易的帳本及執行結果達成一致共識。
驗證者節點會處理這些交易及將它們包含在本地的區塊鏈資料庫的副本。這表示最新的驗證者節點會在本地維持到一個最新狀態的區塊鏈副本。

驗證者節點透過私密網路直接與其他驗證者節點溝通。完整節點是外部驗證及(或)資源傳播的最終交易的歷史記錄。
他們能夠從其他具相同性質的節點接收交易，並且可以在本地重新執行相關數據（與驗證者節點執行交易的方式相同）。
完整節點會將重新執行交易的結果儲存到本地儲存位置。在整個過程中，他們可以隨時挑戰驗證者的任何犯規行為，及針對是否曾經試圖重寫或修改區塊鏈歷史紀錄的情況提供證據。這有助減輕驗證者節點的腐敗及(或)共謀作惡。

### 2024.09.18
#### 驗證節點的組成
* Mempool:
Mempool保存了已提交到區塊鏈但尚未達成一致或執行的交易在記憶體緩衝區的一個元件。
在這個緩衝區能夠在驗節點和完整節點之間複製。

在完整節點的JSON-RPC服務會將交易傳送到驗證節點的mempool。
然後Mempool對交易進行不同檢查，以確保交易的有效性及防止DOS攻擊。
當新交易通過初始驗證並添加到mempool時，它會即時被分發到網路中其他驗證節點的mempool。

當驗證節點暫時成為共識協議中的領導者時，共識會從mempool中提取一組交易，然後提出一個新的交易區塊。
之後該區塊會被傳送給其他驗證者，並包含該區塊中所有交易的總次序。
然後每個驗證者執行該區塊及對會否接受新的區塊所提出的提案進行投票。

* 共識(consensus):
共識是負責對交易區塊進行排序並透過與網路中的其他驗證器節點參與共識協議來就執行結果達成一致的元件。

* 執行 (execution)
執行是協調交易區塊的執行及維持短暫狀態的元件。共識投票會在短暫狀態進行，執行會在記憶體請求中維持一個執行結果，
直到達成共識及將該區塊提交到分布式資料庫為止。
執行使用虛擬機器來執行交易。執行的部分會充當系統輸入(以交易形式表示)、儲存(提供持久層)和虛擬機器(用於執行)之間的glue layer。

* 虛擬機器（Virtual machine）
用於執行每個交易內的Move程式及確定執行結果。節點的mempool使用虛擬機器對交易進行驗證檢查，
而執行會使用虛擬機器來執行交易。

* 儲存 (storage)
儲存元件用於將已確定的交易區塊及其執行結果持續地存在到本機數據庫。

* 狀態同步裝置(State synchronizer)
節點利用其狀態同步裝置元件來「趕上」區塊鏈的最新狀態和維持最新狀態。

### 2024.09.19
昨天參與了共學的線上活動，了解到Aptos的代幣標準，及合約相關的編寫。

```
module my_addr::fungible_asset_example {
    use aptos_framework::fungible_asset::{Self, MintRef, TransferRef, BurnRef, Metadata, FungibleAsset};
    use aptos_framework::object::{Self, Object};
    use aptos_framework::primary_fungible_store;
    use std::error;
    use std::signer;
    use std::string::utf8;
    use std::option;
  
  const ASSET_SYMBOL: vector<u8> = b"FA";
 
	// Make sure the `signer` you pass in is an address you own.
	// Otherwise you will lose access to the Fungible Asset after creation.
  entry fun init_module(admin: &signer) {
    // Creates a non-deletable object with a named address based on our ASSET_SYMBOL
    let constructor_ref = &object::create_named_object(admin, ASSET_SYMBOL);
    
    // Create the FA's Metadata with your name, symbol, icon, etc.
    primary_fungible_store::create_primary_store_enabled_fungible_asset(
        constructor_ref,
        option::none(),
        utf8(b"FA Coin"), /* name */
        utf8(ASSET_SYMBOL), /* symbol */
        8, /* decimals */
        utf8(b"http://example.com/favicon.ico"), /* icon */
        utf8(b"http://example.com"), /* project */
    );
    
    // Generate the MintRef for this object
    // Used by fungible_asset::mint() and fungible_asset::mint_to()
		let mint_ref = fungible_asset::generate_mint_ref(&constructor_ref)
		
    // Generate the TransferRef for this object
    // Used by fungible_asset::set_frozen_flag(), fungible_asset::withdraw_with_ref(),  
    // fungible_asset::deposit_with_ref(), and fungible_asset::transfer_with_ref().
		let transfer_ref = fungible_asset::generate_transfer_ref(&constructor_ref)
		
    // Generate the BurnRef for this object
    // Used by fungible_asset::burn() and fungible_asset::burn_from()
		let burn_ref = fungible_asset::generate_burn_ref(&constructor_ref)
    
    // Add any other logic required for your use case.
    // ...
  }
}
```

<!-- Content_END -->