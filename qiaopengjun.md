---
timezone: Asia/Shanghai # 北京时间 (UTC+8)
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# {你的名字}

1. 自我介绍
    Qiao Pengjun 乔鹏军。有Python、Go、Rust、solidity的开发经验。大约是去年开始了解Web3，最近在学习solidity。对区块链技术很感兴趣。了解了一点Solana、Sui、Starknet... 正在继续学习。希望本次学习能让我更深入的了解Web3。拥抱Web3，拥抱未来。
2. 你认为你会完成本次残酷学习吗？
   我认为我会完成本次残酷学习，因为我有信心，并且我相信我能够克服任何困难。

## Notes

<!-- Content_START -->

### 2024.09.07

Aptos 区块链上的每个账户都由一个 32 字节的账户地址标识。
与其他区块链中账户和地址隐式不同，Aptos 上的账户是显式的，需要先创建才能执行交易。
可以通过将 Aptos 代币 (APT) 转移到 Aptos 来显式或隐式创建账户。

Aptos 上有三种类型的账户：

标准账户——这是一个典型的账户，对应一个地址和一对相应的公钥/私钥。
资源账户- 一个没有对应私钥的自主账户，供开发者存储资源或上链发布模块。
对象- 存储在代表单个实体的单个地址内的一组复杂资源。

帐户地址为 32 字节。它们通常显示为 64 个十六进制字符，每个十六进制字符为一个半字节。有时地址以 0x 为前缀。
Aptos区块链默认采用Ed25519签名交易。

Aptos 区块链存储三种类型的数据：

交易：交易表示区块链上的账户正在执行的预期操作（例如转移资产）。
状态：（区块链账本）状态代表交易执行输出的累积，即存储在所有资源内的价值。
事件：交易执​​行时发布的辅助数据。
只有交易才能改变账本状态。

<https://aptos.dev/en/build/get-started/developer-setup>

Install the Aptos CLI on Mac

```bash
brew update
brew install aptos

aptos help

brew update
brew upgrade aptos

intensive-colearning-aptos on  main via 🅒 base took 4.3s 
➜ aptos --version              
aptos 4.1.0


Code/Aptos/hello_aptos via 🅒 base
➜
aptos init
Configuring for profile default
Choose network from [devnet, testnet, mainnet, local, custom | defaults to devnet]
devnet
Enter your private key as a hex literal (0x...) [Current: None | No input: Generate new key (or keep one if present)]

No key given, generating key...
Account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 doesn't exist, creating it and funding it with 100000000 Octas
Account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 funded successfully

---
Aptos CLI is now set up for account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 as profile default!
 See the account here: https://explorer.aptoslabs.com/account/0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35?network=devnet
 Run `aptos --help` for more information about commands
{
  "Result": "Success"
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 1m 32.7s
➜
aptos account list
{
  "Result": [
    {
      "0x1::account::Account": {
        "authentication_key": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
        "coin_register_events": {
          "counter": "0",
          "guid": {
            "id": {
              "addr": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
              "creation_num": "0"
            }
          }
        },
        "guid_creation_num": "2",
        "key_rotation_events": {
          "counter": "0",
          "guid": {
            "id": {
              "addr": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
              "creation_num": "1"
            }
          }
        },
        "rotation_capability_offer": {
          "for": {
            "vec": []
          }
        },
        "sequence_number": "0",
        "signer_capability_offer": {
          "for": {
            "vec": []
          }
        }
      }
    }
  ]
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 2.5s
➜
aptos account fund-with-faucet --account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35
{
  "Result": "Added 100000000 Octas to account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35"
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 2.8s
➜
touch StudyAptosNotes.md
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base
➜
open -a Typora StudyAptosNotes.md
                                                                                                                                              


Code/Aptos/hello_aptos via 🅒 base
➜
ls
StudyAptosNotes.md assets

Code/Aptos/hello_aptos via 🅒 base
➜
ls -a
.                  ..                 .aptos             StudyAptosNotes.md assets

Code/Aptos/hello_aptos via 🅒 base
➜
cd .aptos/

Aptos/hello_aptos/.aptos via 🅒 base
➜
ls
config.yaml

Aptos/hello_aptos/.aptos via 🅒 base
➜
c
```

<https://aptos.dev/en/build/cli/install-cli/install-cli-mac>
<https://www.youtube.com/watch?v=_EFoVYcrbiY>
<https://plugins.jetbrains.com/plugin/14721-move-on-aptos>
<https://move-developers-dao.gitbook.io/aptos-move-by-example>
<https://marketplace.visualstudio.com/items?itemName=movingco.move-analyzer-plus>
<https://www.youtube.com/watch?v=87eeYsstBD4>

### 2024.09.08

[idea 配置 aptos](https://docs.pontem.network/02.-move-language/intellij_ide_extension)

创建项目

```bash
mkdir hello_optos
cd hello_aptos
```

初始化项目

```bash
aptos move init --name hello_aptos
```

初始化账户

```shell
aptos init
```

编译

```shell
aptos move compile
```

测试

```shell
aptos move test
```

部署

```shell
aptos move publish --named-address hello_aptos
➜ aptos move publish --named-addresses my_addrx=3b551727cac1bd5dc45023b869c9e37dd9e1830fc02ffe32f19597a668ba906d
```

运行

```shell
aptos move run --function-id 0x1::hello_aptos::greet --args "hello"
```

### 2024.09.09

Move 语言与变量
变量是什么？
变量是存储数据值的容器，可以用来存储和操作数据。在 Move 语言中，变量可以用来存储整数、布尔值、字符串等数据类型。
变量：是有名字的对象
对象：存储某个类型值的内存区域
值：按照类型进行解释的bytes集合
类型：定义可能值的操作
类型系统：定义类型和值之间的关系
值类型是如何存储的？
值类型，意为简单的类型，其主要特征是数量量较小，常见有以下类型：
布尔类型
整数
浮点数
枚举
字符串
堆类型值的指向
...

引用类型是如何存储的？
引用类型，意为复杂类型，其主要特征是数量量较大，常见有以下类型：
结构体
数组
向量
函数
模块
对象
类
...

Move 语言中的变量是如何存储的？
Move 语言中的变量分为值类型变量和引用类型变量，它们的存储方式有所不同。
值类型变量：直接存储在栈上，不需要额外的内存分配。
引用类型变量：存储在堆上，需要通过引用来访问。

值类型与引用类型的关系
通常我们定义一个变量为对象时，其对象的值存储在堆上，其堆内存的索引存储在栈上，用栈上的索引指向堆上存储的引用类型数据。

Move 的核心差异之一
在值类型与引用类型关系上，不同于其他语言的索引方式。而是以“所有权”来作为引用类型的操作。

1. 所有权只能同时由 1 “人” 拥有
2. 所有权以转移的形式流转给其他变量

这样做有什么好处？

1. 避免内存泄露，不同于其他语言，在编译阶段就可以告知什么时候可以回收内存
2. 提高内存使用效率，避免对引用类型的不必要拷贝
3. 更好的可读性和可维护性

### 2024.09.10

UINT/ STRING/ BOOL 与 ADDRESS 四大类型

```rust
module 0x42::Types {
    use std::debug::print;
    use std::string;
    use std::string::{String, utf8};

    #[test]
    fun test_num() {
        let num_u8: u8 = 42; // 0~2**8-1
        let num_u8_2 = 43u8;
        let num_u8_3 = 0x2A; // hash

        let num_u256: u256 = 100_000;

        let num_sum = (num_u8 as u256) + num_u256;
        print(&num_u8);
        print(&num_u8_2);
        print(&num_u8_3);
        print(&num_u256);
        print(&num_sum);
    }

    #[test]
    fun test_bool() {
        let bool_true: bool = true;
        let bool_false: bool = false;
        print(&bool_true);
        print(&bool_false);
        print(&(bool_true == bool_false));
    }

    #[test]
    fun test_string() {
        let str: String = utf8(b"Hello, Move!");
        print(&str);
    }

    #[test]
    fun test_addr() {
        let addr: address = @0x42;
        let addr_2: address = @0x00000000000000000000000000000000000000000A;

        print(&addr);
        print(&addr_2);
    }
}

```

### 2024.09.11

APTOS-MOVE
VECTOR 向量核心特性 1
基础概念
Vector（向量）类似其它语言中的数组， 内部存储的是同一类型的数据。

| 语法              | 描述                 |
| ----------------- | -------------------- |
| vector[]          | 空数组               |
| vector[e1,...,en] | 具有同类型元素的数组 |

增删改查功能

<https://aptos.dev/en/build/smart-contracts/book/vector>

函数修饰符
核心概念
函数修饰符是用来赋予函数特殊能力的一组关键字。主要有以下几类

- 可见性
  - 无Public，私有函数，仅限 module 内部调用
  - friend public，模块内部函数，同包模块之间可以调用
  - Public，模块公开函数，所有模块都可以调用
- 全局存储引用
  - acquires，当需要使用 move_from，borrow_global，borrow_global_mut 访问地址下的资源的时候，需要使用 acquires 修饰符
- 链下
  - entry，修饰后，该方法可由链下脚本调用

### 2024.09.12

APTOS-MOVE
STRUCT 特性解读
核心概念
Aptos Move 的 Struct 结构体用于存储结构化数据。Struct 可以相互嵌套，并可以作为资源存储在特定地址下。”

1. 命名必须以大写字母开头
2. 可以通过 has 关键字赋予能力

```rust
struct Person {
  ape: u8,
  birthday: u32,
}

struct People {
  people: vector<Person>,
}
```

修饰符
Copy - 值能够被复制
Drop - 值可以在作用域结束时被自动清理
Key - 值可以用作于全局存储的键 Key
Store - 值可以存储在全局存储中

除 Struct 类型外，其他的类型默认具备 store、drop、copy 的能力，Struct 最终是存储在用户的地址上（或者被销毁），不存在 Aptos 合约里，Aptos 合约是一个全纯的函数。

Drop
值能够在使用结束后被销毁

```rust
//drop
struct Coin {
  b: bool
}

#[test]
fun test6() {
  let c = Coin { b: true }; // 会报错
}

//drop
struct Coin has drop {
  b: bool,
}

#[test]
fun test6() {
  let c = Coin { b: true };
}

```

copy
值能够在使用结束后被复制

```rust
//copy
struct CanCopy has drop {
  b: bool,
}

#[test]
fun test5() {
  let c = CanCopy { b: true };
  let c1 = c; // no copy
  let CanCopy { b } = &mut c1;
  *b = false;
  debug::print(&c1.b);
}
```

```rust
// copy
struct CanCopy has copy, drop {
  b: bool,
}

#[test]
fun test5() {
  let c = CanCopy { b: true };
  let c1 = c; // copy
  let CanCopy { b } = &mut c1;
  *b = false;
  debug::print(&c1.b);
  debug::print(&c.b);
}
```

Key
值可以用作于全局存储的键 Key

```rust
//key
struct Coin has key {
  value: u64,
}

public entry fun mint(account: &signer, value: u64) {
  move_to(account, Coin { value });
}

#[test(account = @0x42)]
public fun test_mint(account: &signer) acquires Coin {
  let addr = signer::address_of(account);
  mint(account, 100);
  let coin = borrow_global<Coin>(addr).value;
  debug::print(&coin);
}
```

store
值可以被全局存储，通常配合Key使用

```rust
//store
struct Key has key, drop {
  a: Store,
}

struct Store has store, drop {
  b: bool,
}

#[test]
fun test6() {
  let k = Key {
    a: Store { b: true },
  };
  debug::print(&k.a.b);
}
```

父 的有 Key 子的必须有 stare

```rust
//store
struct Key has key, drop {
  a: Store,
}

struct Store has drop {
  b: bool,
}

#[test]
fun test6() {
  let k = Key {
    a: Store { b: true },
  };
  debug::print(&k.a.b); // 会报错
}
```

<https://aptos.dev/en/build/smart-contracts/book/structs-and-resources>
<https://aptos.dev/en/build/smart-contracts/book/abilities>

### 2024.09.13

函数操作流IF、WHILE、LOOP

```rust
module 0x42::Demo3 {
    use std::debug;

    #[test]
    fun test_if() {
        let x = 5;
        let x2 = 10;
        if (x == 5) {
            debug::print(&x);
        } else {
            debug::print(&x2);
        }
    }

    #[test]
    fun test_while() {
        let  x = 0;
        while (x < 10) {
            debug::print(&x);
            x = x + 1;
        }
    }

    #[test]
    fun test_while2() {
        let  x = 5;
        while (x < 10) {
            debug::print(&x);
            x = x + 1;

            if (x == 7) {
                break;
            }
        }
    }

    #[test]
    fun test_while3() {
        let  x = 5;
        while (x < 10) {
            x = x + 1;
            if (x == 7) {
                continue;
            };
            debug::print(&x);
        }
    }

    #[test]
    fun test_loop() {
        let x = 5;
        loop {
            x = x + 1;
            if (x == 7) {
                break;
            };
            debug::print(&x);
        }
    }

    #[test]
    fun test_loop2() {
        let x = 5;
        loop {
            x = x + 1;
            if (x == 7) {
                continue;
            };
            if (x == 10) {
                break;
            };
            debug::print(&x);
        }
    }
}
```

模块的特性
引用
可以通过以下三种方式导入模块，用来更好的进行管理。注意命名不能重复。

```rust
use std::debut;
use std::debug::print;
use std::debug::{print as P, native_print, print};

fun main() {
  debug::print(&v);
  print(&v);
  P(&v);
}
```

作用域
可以在全局定义，也可以定义在函数内部，只在所在的作用域内有效。

```rust
fun main() {
  use std::debug::print;
  print(&v);
}

public(friend) 
声明当前模块信任用模块，受信任模块可以调用当前模块中具有 public(friend) 的可见性函数

public
声明当前模块对外供其他接口调用的方法。

entry
声明可被链下调用的模块方法。

模块的发布与交互
发布流程
1. 配置账户，并为其发送 gas
  可以通过 aptos init 来初始化一个账户。
2. 编译并测试模块
  可以通过以下命令来编译
  aptos move compile --named-addresses hello_blockchain=default
3. 发布模块
  aptos move publish --named-addresses hello_blockchain=default

交互流程
1. 区块链浏览器
  https://explorer.aptoslabs.com/
2. 终端
  aptos move run --function-id 'default::message::set_message' --args 'string:hello, blockchain'

3. SDK
  https://aptos.dev/en/build/sdks

### 2024.09.14

认识 OBJECT
什么是 Aptos object？
1. 对象是单个地址的资源容器，用于储存资源
2. 对象提供了一种集中式资源控制与所有权管理的方法

创建并转移对象实例
我们可以通过 aptos_framework 库下的 object 来实现对象的功能。
```rust
module my_addr::object_playground {
  use std::signer;
  use aptos_framework::object::{self, ObjectCore};

  entry fun create_and_transfer(caller: &signer, destination: address) {
    // Create object
    let caller_address = signer::address_of(caller);
    let constructor_ref = object::create_object(caller_address);

    // Set up the object

    // Transfer to destination
    let object = object::object_from_constructor_ref<ObjectCore>(&constructor_ref);
    object::transfer(caller, object, destination);
  }
}
```

两类对象
可删除普通对象
不可删除对象

- 命名对象，通过固定的 signer 和特定的 seed 生成唯一地址的对象，1个地址只能生成1个
- 粘性对象，通过 signer 生成的对象，1个地址可以生成多个
  
### 2024.09.15

OBJECT 配置与使用
object 有哪些配置？

1. 扩展对象：将对象变成可动态配置的，可以往里面添置新的 Struct 资源
2. 转移管理：可以开启或者禁用 object transfer 功能
3. 受控转移：仅可使用一次转移功能
4. 允许删除：允许删除对象

### 2024.09.16

DApp(Decentralized Application)

- 与(Centralized) App 的差异
  - 资产的所有权
  - 运行在区块链上
- 客户端 + 智能合约
  - Web browser / iOS / Android
  - Move Language Smart Contracts

JavaScript / TypeScript

- Javascript 基础
  - <https://developer.mozilla.org/en-US/docs/Web/JavaScript>

- Typescript 官网
  <https://www.typescriptlang.org/docs/>
  <https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html>
- Typescript Playground
  
DApp 基本业务流程

- 将 DAPP 与钱包相连接
- 查看当前账号信息
- 与合约交互
- 获取合约内的数据

### 2024.09.17

如何与 Aptos 链交互
区块链是个数据库

- CRUD
- 数据提交：Transaction 提交
- 数据查询：查询链上数据
- 提交 Transaction 有几种方法？

Transaction 提交

- Aptos CLI
  - aptos move run
- 在浏览器直接提交
  - <https://explorer.aptoslabs.com/>
  - Mainnet/Testnet/Devnet 的区别？
- 使用 SDK <https://aptos.dev/en/build/sdks>
  - Rust
  - Python
  - TypeScript
  - ...
- Gas fee

链上数据查询 - FullNode

- 什么是 FullNode(FN)
  - 提供 Restful API
  - <https://fullnode.devnet.aptoslabs.com/v1/spec#/>
  - <https://fullnode.testnet.aptoslabs.com/v1/spec#/>
- view Function
  - 什么是 view Function
  - CLI + SDK
  - 浏览器
- 链上数据查询 - Indexer
  - 什么是 Indexer
  - 为什么需要 Indexer
    - 区块链是一个 日志型数据库
    - 聚合和反查需求是非常常见的
  - GraphQL

链上数据查询 - GraphQL

- 一种声明式的查询语言，对标 Restful
- 来自 Facebook
- 优点：
  - 所取即所得，精准获取
  - 具有类型系统，可以避免很多错误
  - 解放前后端，前端可以自己定义查询，后端只需要提供接口
- 缺点：
  - 学习曲线陡峭
  - 不直观，工具支持少
  - 性能瓶颈
  - 安全风险
<https://aptos.dev/en/build/indexer/aptos-hosted>
<https://aptos.dev/en/build/indexer/self-hosted>

常见开发范式

- 前端 - 合约
- 前端 - 合约 - Indexer
- 后端呢？
最佳实践
- 数据流定义先行
- 幂等 实现很重要
- 奥卡姆剃刀-慎重引入后端

随机性

1. 链上原生方法
2. 链外引入
3. 伪随机

Mint 发售的要素

1. 支付
2. 铸造
3. 开关(时间)
4. 盲盒

### 2024.09.18

object::ExtendRef
理解为 object 的 signer
把 object 理解为一个 account
有 object signer 才能 move to 存储 struct
extendRef 为了 signer 这个可以被合约管理，抽象出来一个 Ref ，可以用来获得 object signer
ExtendRef 类型可以生成 对应内部 Object 地址的 Signer 类型的实例
signer 只有 drop 能力，不能 store

Creating an Object involves two steps:

Creating the ObjectCore resource group (which has an address you can use to refer to the Object later).
Customizing how the Object will behave using permissions called Refs.

### 2024.09.19

entry 方法调用者是 钱包地址 也是 signer
合约在发布的时候内部去调用的， 它只能自己去初始化，不能被外部调用， init_mode signer 是合约
Move.toml 是 Move 项目中的配置文件，负责管理依赖项和地址。对于像 @contract 和 @user 这样的命名地址，你需要在 Move.toml 文件中通过 [addresses] 或 [dev-addresses] 部分指定一个实际的值。否则，Move 编译器将无法解析这些地址，导致编译失败。

当你在代码中使用像 @contract 或 @user 这样的命名地址时，这些地址必须在 Move.toml 文件中通过 [addresses] 声明一个实际的地址值。原因如下：

 1. 命名地址的解析：Move 语言允许你使用命名地址（如 @contract）来提高代码的可读性和可移植性。这些命名地址并不直接对应链上的某个具体地址，它们只是占位符。你需要在 Move.toml 文件中将这些命名地址映射到具体的链上地址。
 2. 编译器要求：Move 编译器需要知道所有命名地址的实际值才能正常编译代码。Move.toml 文件的 [addresses] 部分用于声明这些地址的实际值，或者在开发模式下，使用 [dev-addresses] 来生成临时的开发地址。

### 2024.09.20

token::create_named_token
token::create
<https://aptos.dev/zh/build/apis>

```rust
module red_packet::red_packet {
    use aptos_framework::fungible_asset::{Self, MintRef, TransferRef, BurnRef};
    use aptos_framework::object::{Self, Object};
    use aptos_framework::primary_fungible_store;
    use std::signer;
    use std::string::utf8;
    use std::option;

    #[test_only]
    use aptos_framework::account;

    const SEED: vector<u8> = b"RedPacketFA";

    struct MyMintRef has key {
        admin: address,
        mint_ref: MintRef
    }

    struct MyTransferRef has key {
        transfer_ref: TransferRef
    }

    struct MyBurnRef has key {
        burn_ref: BurnRef
    }

    fun init_module(admin: &signer) {
        let constructor_ref = object::create_named_object(admin, SEED);

        primary_fungible_store::create_primary_store_enabled_fungible_asset(
            &constructor_ref,
            option::none(),
            utf8(b"RedPacketFA Coin"),
            utf8(b"RPFA"),
            8,
            utf8(b"https://aptos.dev/docs/aptos-black.svg"),
            utf8(b"https://github.com/qiaopengjun5162")
        );

        let mint_ref = fungible_asset::generate_mint_ref(&constructor_ref);

        let transfer_ref = fungible_asset::generate_transfer_ref(&constructor_ref);

        let burn_ref = fungible_asset::generate_burn_ref(&constructor_ref);

        move_to(
            admin,
            MyMintRef { admin: signer::address_of(admin), mint_ref }
        );

        move_to(admin, MyBurnRef { burn_ref });

        move_to(admin, MyTransferRef { transfer_ref });
    }

    entry fun mint(sender: &signer, amount: u64) acquires MyMintRef {
        let my_mint_ref = borrow_global<MyMintRef>(@red_packet);
        let fa = fungible_asset::mint(&my_mint_ref.mint_ref, amount);
        primary_fungible_store::deposit(signer::address_of(sender), fa);
    }

    /// Check if the given signer is the admin.
    public fun is_owner(owner: &signer): bool acquires MyMintRef {
        let my_mint_ref = borrow_global<MyMintRef>(@red_packet);
        return my_mint_ref.admin == signer::address_of(owner)
    }

    #[view]
    /// Get the balance of `account`'s primary store.
    public fun balance<T: key>(account: address, metadata: Object<T>): u64 {
        primary_fungible_store::balance(account, metadata)
    }

    #[view]
    public fun is_balance_at_least<T: key>(
        account: address, metadata: Object<T>, amount: u64
    ): bool {
        primary_fungible_store::is_balance_at_least(account, metadata, amount)
    }

    #[test]
    fun test() acquires MyMintRef {
        let user_signer = account::create_account_for_test(@red_packet);
        init_module(&user_signer);

        let user1_signer = account::create_account_for_test(@0x12345);
        mint(&user1_signer, 1 * 1000 * 1000 * 100);
    }
}

```

### 2024.09.21

<https://www.youtube.com/watch?v=bny8hBEpBmw>
Resource Group & Object Model

Resource Group
底层存储系统
更优化的使用存储系统， 节省gas费
ledger 完全二叉树  Transaction 叶子节点 Merkle Tree 共识
tree 链  证明 缺点 中间节点
区块的概念只存在于共识
Transaction hash + 状态树 +  Event Tree = TransactionInfo
key = Hash(Account address, Access path)
Value = Serialized byte array
resource_group module address global
Only struct and fun can have attributes
手动调整 Gas Cost

Flow of Object Creation

```rust
// 1. Create ConstructorRef
let object_cref: ConstructorRef = object::create_object(aaron_address);
let object_signer = generate_signer(&object_cref);
move_to(&object_signer, X {});
```

object convert
有些 object 是不能被删除的
Move
类型系统

- 将一个语言中所有能表达的值分类成一个个子集
- 调用的时候就可以通过规定实现方只能接受哪种子集
传统语言结构
- 语言
- 编译器
- 执行码 LLVM jvm
编译器完成类型检查
- 静态检查保证类型正确
- 运行时不再检查
- 所以字节码不需要保留类型信息
智能合约不同于传统程序
- 合约调用方被调用方不一定由同一作者完成
- 为什么 Solidity 中没有结构体呢？
Move 不同于 Solidity
- 字节码中保留了类型信息
- 上链代码保证互相的类型安全

### 2024.09.22

<https://www.youtube.com/watch?v=wlbHrHtvyIk>
在 Aptos 上实现简单的 NFT 市场
交易市场的实现逻辑
目标：要实现一个简单的 NFT 市场
首先要考虑：

1. NFT存放在哪里
2. 挂单的信息存放在哪里
3. 用户如果购买/取消

#### 用户可以挂单/ 取消/ 购买NFT

#### 1. NFT存放在哪里

   NFT 是可以存储起来的

- Table
- Vector
  NFT 存放在用户的资源下
  用 Table 保存所有挂单状态的NFT

```rust
struct Token has store {
  id: TokenId,
  amount: u64,
}
```

#### 2. 挂单的信息存放在哪里

   用户挂单时需要输入

1. 挂单的NFT 的 TokenId
2. 数量和价格
   如果将这些信息存储起来

#### 3. 用户如何购买和取消

购买：

- 需要知道挂单者的地址
- 需要知道挂单 Token Id 以及价格
取消：
- 必须是自己的挂单
- 需要知道挂单 Token Id

为什么需要知道挂单者的地址
合约的存储结构
挂单者 NFT TokenStoreEscrow  取出NFT  购买者
挂单者 挂单信息 TokenListings 查看挂单信息检查妇科 购买者

代码详解

- 交易市场的实现 Listing
组合 Token Id
取出要挂单的NFT
卖家是否挂过单，没有则发放一个挂单集合的结构
将 NFT 放入挂单集合结构中
将挂单信息存放到 Table

- 交易市场的实现 Cancel
从全局存储中找到自己的挂单信息集合
组合 Token Id
判断是否有挂单状态
删除挂单信息
从全局存储中找到自己的挂单 NFT 集合
判断是否有这个 NFT
取出NFT
将NFT 放入钱包

- 交易市场的实现 Buy
组合 Token Id
从全局存储中找到卖家的挂单信息集合
检查金额是否充足
从全局存储中找到卖家的挂单 NFT 集合
检查购买的金额是否满足
检查挂单的 NFT的数量是否满足
取出NFT
将 NFT 发送到买家钱包
将购买的金额发送到卖家钱包
如果买空则销毁挂单信息

mint_ref 就是铸币权
看你怎么用它
mint_ref 理解为一个实体，一把钥匙，这个钥匙只能开 Mint() 这个函数
你的合约要做的就是把这个钥匙找一个位置放起来

至于这把钥匙

- 放在门口地垫下面（每个人都能拿到）
- 放在自己身上 （自己能拿到）
- 放在银行保险柜 （自己也拿不到）

是合约要实现的逻辑
Token 的元数据是 Object<Metadata> ，FA 的实体是 FungibleAsset
Object<Metadata> 相当于 Solidity 中的 Token 地址
FungibleAsset  是实例、资源、纸币的实体，不仅仅是数字

### 2024.09.23

[pontem](https://playground.pontem.network/)
<https://www.youtube.com/watch?v=r9KDv-_j16A>
Aptos：Move 语言初探
目录

- Move 起源
- 现今智能合约的问题
- Move 的改善
- Demo

Move 起源

- Move是一种基于 Rust 的语言
- 起初是专门为 Meta 的区块链项目 Diem 开发的
- 目的是需要一种可以精准描述资产的语言
- 愿景是希望成为区块链语言的 JavaScript

资产定义
稀缺性
应控制系统中的资产供应，复制现有资产应当被禁止，且创建新资产应该为一种特权
资产所有权的权限管理
系统中的参与者资产应该能受到资产控管条例的保护
现今智能合约的问题
稀缺性是不可扩展的

- 原生代币的稀缺性：区块链的原生代币（ETH...）通常具有内建的稀缺性机制
- 智能合约代币的问题：但这种稀缺性无法直接扩展到基于智能合约创建的代币（如 ERC-20 代币）
- 手动实现的风险：开发者必须手动实现稀缺性逻辑，这增加了出错和安全漏洞的风险

```rust
function transfer(address to, uint256 amount) public {
    require(balance[msg.sender] >= amount, "Insufficient balance");
    balance[msg.sender] -= amount;
    balance[to] += amount * 2; // 接收者获得两倍数量，违法稀缺性
}
```

资产所有权

- 资产不存在用户的钱包中，而是透过智能合约的状态分配
重入攻击(Reentrancy Attack)
- 你只有一笔存款，但你却可以提款两次

```rust
function withdraw(uint256 amount) public {
    require(balance[msg.sender] >= amount, "Insufficient balance");
    balance[msg.sender] -= amount;
    (bool success, ) = msg.sender.call{value: amount * 2}("");
    require(success, "Transfer failed");
}

function withdraw(uint256 amount) public {
    require(balance[msg.sender] >= amount, "Insufficient balance");
   
    (bool success, ) = msg.sender.call{value: amount }("");
    require(success, "Transfer failed");
     balance[msg.sender] -= amount;
}
```

Move 的改善
资源（Resource）导向

- 资源作为一等公民，具有自己的生命周期和规则

```rust
struct CoinStore<phantom CoinType> has key {
  coin: Coin<CoinType>,
}

struct Coin<phantom CoinType> has store {
  value: u64,
}
```

- 所有权明确定义

```rust
public fun transfer_coin<CoinType> (
  from: &mut CoinStore<CoinType>,
  to: &mut CoinStore<CoinType>,
  amount: u64,
) {
  let coin = withdraw(&mut from.coin, amount);
  deposit(&mut to.coin, coin);
}
```

- 编译时检查
能力属性定义
ability 定义
Key 允许一个类型直接存在于区块链上，并且存属于特定的账户
store 允许一个值被存储在区块链的全局状态中或作为其他结构的一部分
copy 允许一个值在区块链上被复制，而不仅是被移动
drop 允许一个值在区块链上被丢弃，无需特别处理
环境准备
- Aptos CLI
- Aptos TypeScript SDK
- Aptos Wallet Adapter
- Create React App
- node and npm
网络
Mainnet
- APT 的价值： 有价值， 不能乱花
- 保存期限：永久
Testnet
- APT 的价值： 随便花
- 保存期限：永久
Devnet
- APT 的价值： 随便花
- 保存期限：每个礼拜刷新
DEMO
在 Aptos Move 中，init_module 是模块的初始化函数，用于在模块部署时执行一些必要的初始化逻辑。例如，创建资源、配置模块的初始状态等。如果你的模块不需要执行这些初始化操作，那么你可以选择不写 init_module。
 • 如果模块需要在部署时执行某些操作，则必须写 init_module。
 • 如果没有初始化需求，init_module 可以不写。
exists<T>(address) 是 Move 中的一个内置函数，它用来判断某个地址上是否已经存储了某种类型的资源（T 类型）。

在 Move 中生成签名者 (`signer`) 的主要原因是为了确保操作权限和安全性。签名者是代表一个地址或者对象进行交易的实体，拥有该地址或对象的授权。因此，生成签名者的主要作用是为了控制特定资源或对象的访问权限，确保只有合法的实体才能操作它们。

### 具体原因包括

1. **权限控制**：
   - `signer` 是 Move 中用来授权对资源或对象执行敏感操作的机制。只有持有合法 `signer` 的人，才能对相关的资源进行修改或交互操作。
   - 生成对象的 `signer` 可以确保后续对该对象的操作是经过授权的，防止未经授权的访问或操作。

2. **安全性**：
   - 在链上操作时，所有操作都是公开的。通过使用签名者，可以验证每个操作的合法性。生成的签名者可以确保只有特定的用户或特定对象持有的权限才能修改对象状态。
   - 例如，当一个用户创建了一个 `TodoList` 对象，生成该对象的签名者可以用来确保只有这个 `TodoList` 的拥有者才能修改或删除它。

3. **资源所有权的确认**：
   - 在 Move 中，资源的所有权是一个核心概念，资源永远不能被复制或丢弃。通过生成与对象关联的签名者，可以证明某个地址或对象对资源的拥有权。
   - 如果你想操作某个对象的内部状态，比如修改其中的数据，生成该对象的签名者是证明你拥有该对象并有权操作它的方式。

4. **对象的独立性**：
   - 每个对象都可以有自己独立的签名者，这意味着对象本身可以有授权执行的行为。生成签名者的目的是赋予对象权限，以便对象本身可以执行与其相关的操作。
   - 例如，一个 `TodoList` 对象可以有自己的签名者，确保只有该对象的所有者或创建者才能对其进行修改或操作。

### 实例化对象签名者的场景

- 当你创建一个新对象时（比如 `TodoList`），可能需要后续操作来修改、删除或添加数据。通过生成对象签名者，后续对该对象的操作必须通过该签名者来进行，这确保了对象的操作权限只授予了正确的实体。
- 如果你允许其他用户在对象中执行某些操作（如共享资源或分配任务），你可能会根据该签名者的权限控制他们能做什么。

### 举例

在你的代码中，生成 `obj_holds_todo_list` 对象的签名者后，可以在后续操作中，用该签名者来执行对 `TodoList` 的更新操作。例如，当你想要添加一项任务到 `TodoList` 中时，只有通过持有正确签名者的用户才可以进行操作，防止其他用户对不属于自己的 `TodoList` 进行修改。

总结来说，生成签名者是为了确保操作权限、安全性、资源所有权的确认以及对象的独立性。通过签名者机制，可以有效地管理链上对象和资源的访问和操作权限。

### 2024.09.24

let signer_cap = resource_account::retrieve_resource_account_cap(swap_signer, @deployer);
这个是需要手动创建一个 resource account
因为老版的 Coin 必须通过当前合约创建
现在的 FA 应该没有这个问题了

Aptos Prover
Aptos test
aptos move test
ensures
在 Aptos Move 中，`ensures` 是一个用于函数规范的关键字，确保某个条件在函数执行结束后保持为真。它通常用于智能合约中的验证，以确保在函数执行前后保持状态的一致性。`ensures` 关键字和前置条件的 `requires` 类似，但 `ensures` 主要用于定义函数执行后的状态。

以下是一个简单的 Aptos Move 代码示例，展示如何使用 `ensures`：

```move
module Example {

    struct User has key {
        balance: u64,
    }

    public fun add_funds(user: &mut User, amount: u64) {
        let old_balance = user.balance;
        user.balance = old_balance + amount;

        // Ensures that the balance has increased by the expected amount
        ensures user.balance == old_balance + amount;
    }
}
```

### 解释说明

- `ensures` 在这里用于确认函数 `add_funds` 执行完毕后，用户的余额 `balance` 增加了 `amount`。
- 如果 `ensures` 中的条件在函数结束后不为真，Move 验证器将抛出一个错误。

在 Move 中，`ensures` 帮助开发者在智能合约中保持逻辑的正确性，确保状态更新符合预期，防止逻辑错误或意外行为。

### 使用 `ensures` 的主要目的

1. **验证合约执行后的状态**：确保函数执行后的结果符合预期。
2. **增强代码可读性和可靠性**：开发者可以通过这种声明式的方式清晰地表达合约的预期行为。
3. **安全性保证**：通过定义函数执行后的预期状态，确保合约在不同状态转换中的安全性。

这是 Aptos Move 中一种常见的编程模式，特别适用于金融或复杂逻辑的智能合约开发场景。

是的，Aptos Move 中确实有 `assert`，它与 `ensures` 在某些方面类似，都用于验证条件，但它们的作用场景和使用方式不同。

### **`assert` 和 `ensures` 的区别**

1. **`assert` 是运行时检查：**
   - `assert` 在函数执行过程中主动验证某个条件，如果条件不满足，就立即停止执行并抛出错误。
   - 用于在代码中强制检查某些条件，防止不期望的逻辑执行，通常出现在函数执行的中间或某个特定步骤。

   **示例：**

   ```move
   module Example {
       struct User has key {
           balance: u64,
       }

       public fun withdraw_funds(user: &mut User, amount: u64) {
           // 运行时检查：确保余额足够
           assert!(user.balance >= amount, 1); // 如果余额不足，停止执行并抛出错误
           user.balance = user.balance - amount;
       }
   }
   ```

   在这个例子中，`assert` 用于在 `withdraw_funds` 函数中确保用户余额足够，如果不够则终止执行。

2. **`ensures` 是静态验证：**
   - `ensures` 是一个函数执行后使用的后置条件，用于静态验证函数执行结束后某个条件是否满足。它不是在函数执行中进行即时检查，而是用于描述函数在返回时必须保证的状态。
   - 通常用于智能合约的形式化验证，帮助验证器在编译时检查代码逻辑是否正确。

   **示例：**

   ```move
   module Example {
       struct User has key {
           balance: u64,
       }

       public fun add_funds(user: &mut User, amount: u64) {
           let old_balance = user.balance;
           user.balance = old_balance + amount;

           // 确保余额更新后的状态正确
           ensures user.balance == old_balance + amount;
       }
   }
   ```

   在这个示例中，`ensures` 用于确保在 `add_funds` 函数执行完毕后，`user.balance` 的值是正确的。它不是在函数中动态检查，而是帮助 Move 验证器在静态分析阶段确保代码逻辑的正确性。

### **`assert` 和 `ensures` 的使用场景：**

- **`assert`：** 适用于你想在函数运行时强制检查的条件，确保某些状态在运行时不会出错。它通常用来防止一些非法操作，比如转账余额不足等。
  
- **`ensures`：** 主要用于形式化验证（formal verification），确保在函数执行完毕后，合约状态符合预期。在安全性要求较高的合约开发中，`ensures` 提供了额外的保证，尤其是在编译时静态分析阶段。

### 总结

- **`assert`**：运行时条件检查，适用于防止非法操作或逻辑错误。
- **`ensures`**：编译时的后置条件检查，确保函数结束后的状态符合预期，适用于形式化验证和更高层次的安全性保证。

### 2024.09.25

一个人可以拥有多个fungible store 每个store都是一个object。 primary的fungible store是每个账户deterministic的
类似于默认的store
coin的coinstore一个人只能有一个 就是默认的
发布到object的合约，可以在合约内部获取到该object

module SomeAddress::SomeModule {
 ....
}

 @SomeAddress 就是当前合约地址

如果合约是通过 Object 发布的，那么 @SomeAddress 就是 Object 地址/ 合约地址
Object<T> 可以从 address 生成出来
生成时，VM 会检查对应的状态
比如 object::address_to_object<ObjectCore>(object_address) 的时候

vm 会检测 这个 address 是不是一个 object address
如果是一个 object，再检测账户下是否有 <ObjectCore> 这个结构

### 2024.09.26

init_module publish 的时候会自动调用
创建对象的两种方法：
create_named_object
create_sticky_object

```move
module contract::faucet {
    use aptos_framework::fungible_asset::{Self, TransferRef, BurnRef, Metadata, FungibleAsset, MintRef};
    use aptos_framework::object::{Self, Object};
    use aptos_framework::primary_fungible_store;
    use std::string::utf8;
    use std::option;
    use std::signer;
    #[test_only]
    use aptos_framework::account;

    const ASSET_SYMBOL: vector<u8> = b"FA";

    struct MyMintRef has key {
        mint_ref: MintRef
    }

    struct MyTransferRef has key {
        transfer_ref: TransferRef
    }

    struct MyBurnRef has key {
        burn_ref: BurnRef
    }

    fun init_module(contract: &signer) {
        let constructor_ref = object::create_named_object(contract, ASSET_SYMBOL);
        primary_fungible_store::create_primary_store_enabled_fungible_asset(
            &constructor_ref,
            option::none(),
            utf8(b"FA Coin"), /* name */
            utf8(ASSET_SYMBOL), /* symbol */
            8, /* decimals */
            utf8(b"http://example.com/favicon.ico"), /* icon */
            utf8(b"http://example.com"), /* project */
        );

        let mint_ref = fungible_asset::generate_mint_ref(&constructor_ref);


        let transfer_ref = fungible_asset::generate_transfer_ref(&constructor_ref);


        let burn_ref = fungible_asset::generate_burn_ref(&constructor_ref);

        move_to(
            contract,
            MyMintRef {
                mint_ref
            }
        );

        move_to(
            contract,
            MyBurnRef {
                burn_ref
            }
        );

        move_to(
            contract,
            MyTransferRef {
                transfer_ref
            }
        );
    }

    entry fun faucet(
        sender: &signer,
        amount: u64
    ) acquires MyMintRef {
        let my_mint_ref = borrow_global<MyMintRef>(@contract);
        let fa  = fungible_asset::mint(&my_mint_ref.mint_ref, amount);
        primary_fungible_store::deposit( signer::address_of(sender), fa);
    }



    #[test]
    fun test() acquires MyMintRef {
        let user_signer = account::create_account_for_test(@contract);
        init_module(&user_signer);

        let user1_signer = account::create_account_for_test(@0x12345);
        faucet(
            &user1_signer,
            1 * 1000 * 1000 * 100
        );
    }
}

```

### 2024.09.27

笔记内容

### 2024.09.28

笔记内容

### 2024.09.29

笔记内容

### 2024.09.30

笔记内容

### 2024.10.01

笔记内容

### 2024.10.02

笔记内容

### 2024.10.03

笔记内容

### 2024.10.04

笔记内容

### 2024.10.05

笔记内容

### 2024.10.06

笔记内容

### 2024.10.07

笔记内容

### 2024.10.08

笔记内容

### 2024.10.09

笔记内容

<!-- Content_END -->
