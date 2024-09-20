---
timezone: Asia/Shanghai
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

1. 我是一名web2行业的全栈开发，之前参加过波卡、Polygon的黑客松活动，第一次接触Starknet,想学习一下基础知识然后希望可以自己做一个小项目出来。
2. 会的。

## Notes

<!-- Content_START -->

### 2024.09.20

1.学习：https://book.starknet.io/
    Starknet的基础知识学习，
    Cairo语言的了解，
    使用Remix创建合约、编译合约、部署合约、测试合约流程；

Type the library name to see available commands.
------------------------ Declaring contract: lib.cairo ------------------------
{
  "transaction_hash": "0x4a2fcff2f9d066bc3c2becfa1703f28e1eda5c2f8ba42fb529b1403222db415",
  "class_hash": "0x26a91a6327901ef5f9c05a74227560825230124cc0d572c58ce82810d80d46a"
}
---------------------- End Declaring contract: lib.cairo ----------------------
--------------------- Getting declare contract: lib.cairo tx receipt --------------------
{
  "type": "DECLARE",
  "transaction_hash": "0x4a2fcff2f9d066bc3c2becfa1703f28e1eda5c2f8ba42fb529b1403222db415",
  "actual_fee": {
    "unit": "WEI",
    "amount": "0x87c99d770800"
  },
  "messages_sent": [],
  "events": [
    {
      "from_address": "0x49d36570d4e46f48e99674bd3fcc84644ddd6b96f7c741b1562b82f9e004dc7",
      "keys": [
        "0x99cd8bde557814842a3121e8ddfd433a539b8c9f14bf31ebf108d12e6196e9",
        "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
        "0x1000"
      ],
      "data": [
        "0x87c99d770800",
        "0x0"
      ]
    }
  ],
  "execution_status": "SUCCEEDED",
  "finality_status": "ACCEPTED_ON_L2",
  "block_hash": "0x7164753043101015495bbc6a5a8bff85b44cffbe653a028d80338aab77890e7",
  "block_number": 11,
  "execution_resources": {
    "steps": 4339,
    "memory_holes": 112,
    "range_check_builtin_applications": 167,
    "pedersen_builtin_applications": 16,
    "poseidon_builtin_applications": 4,
    "ec_op_builtin_applications": 3,
    "data_availability": {
      "l1_gas": 0,
      "l1_data_gas": 192
    }
  }
}
--------------------- End getting declare contract: lib.cairo tx receipt ------------------
------------------------ Deploying contract: lib.cairo ------------------------
{
  "transaction_hash": "0x4b682a67d108910658ff10ad96f5764f206ae1a170b7bd6d60d9ec16e68d102",
  "contract_address": [
    "0x66a878e6caab8947e409a6936b747e9dfc8de2b0d8a61fd6e5d3b92be206530"
  ]
}
---------------------- End Deploying contract: lib.cairo ----------------------
--------------------- Getting deploy contract: lib.cairo tx receipt --------------------
{
  "type": "DEPLOY",
  "transaction_hash": "0x4b682a67d108910658ff10ad96f5764f206ae1a170b7bd6d60d9ec16e68d102",
  "actual_fee": {
    "unit": "WEI",
    "amount": "0x1c8ee1d89000"
  },
  "messages_sent": [],
  "events": [
    {
      "from_address": "0x41a78e741e5af2fec34b695679bc6891742439f7afb8484ecd7766661ad02bf",
      "keys": [
        "0x26b160f10156dea0639bec90696772c640b9706a47f5b8c52ea1abe5858b34d"
      ],
      "data": [
        "0x66a878e6caab8947e409a6936b747e9dfc8de2b0d8a61fd6e5d3b92be206530",
        "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
        "0x1",
        "0x26a91a6327901ef5f9c05a74227560825230124cc0d572c58ce82810d80d46a",
        "0x1",
        "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
        "0x1ecf5567f308b520e369220843f4159be21f57bb0842123f811f9853b53d157"
      ]
    },
    {
      "from_address": "0x49d36570d4e46f48e99674bd3fcc84644ddd6b96f7c741b1562b82f9e004dc7",
      "keys": [
        "0x99cd8bde557814842a3121e8ddfd433a539b8c9f14bf31ebf108d12e6196e9",
        "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
        "0x1000"
      ],
      "data": [
        "0x1c8ee1d89000",
        "0x0"
      ]
    }
  ],
  "execution_status": "SUCCEEDED",
  "finality_status": "ACCEPTED_ON_L2",
  "block_hash": "0x5af3734e8f438f85525cad6ce4e0806c4a906a19e72d49f163ccb4db2464cfd",
  "block_number": 12,
  "execution_resources": {
    "steps": 9411,
    "memory_holes": 178,
    "range_check_builtin_applications": 313,
    "pedersen_builtin_applications": 31,
    "poseidon_builtin_applications": 5,
    "ec_op_builtin_applications": 3,
    "data_availability": {
      "l1_gas": 0,
      "l1_data_gas": 288
    }
  },
  "contract_address": "0x66a878e6caab8947e409a6936b747e9dfc8de2b0d8a61fd6e5d3b92be206530"
}
--------------------- End getting deploy contract: lib.cairo tx receipt ------------------
------------------- Calling get_owner ------------------------
{
  "resp": [
    "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd"
  ],
  "contract": "lib.cairo",
  "function": "get_owner"
}
------------------- End calling get_owner --------------------
------------------- Calling get_owner ------------------------
{
  "resp": [
    "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd"
  ],
  "contract": "lib.cairo",
  "function": "get_owner"
}
------------------- End calling get_owner --------------------
------------------ Invoking transfer_ownership -----------------------
---------- Invoke transfer_ownership transaction receipt ----------------
{
  "resp": {
    "transaction_hash": "0x24d676258addc3fffbd1118a0403ca7a73e8f676693a635c795873713bb5879"
  },
  "contract": "lib.cairo",
  "function": "transfer_ownership"
}
----------End  Invoke transfer_ownership transaction receipt -------------
----- Getting invoke transfer_ownership transaction details ... ----------
{
  "resultOfTx": {
    "type": "INVOKE",
    "transaction_hash": "0x24d676258addc3fffbd1118a0403ca7a73e8f676693a635c795873713bb5879",
    "actual_fee": {
      "unit": "WEI",
      "amount": "0x193168a90800"
    },
    "messages_sent": [],
    "events": [
      {
        "from_address": "0x66a878e6caab8947e409a6936b747e9dfc8de2b0d8a61fd6e5d3b92be206530",
        "keys": [
          "0x1390fd803c110ac71730ece1decfc34eb1d0088e295d4f1b125dda1e0c5b9ff",
          "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
          "0x56c93bf54e3eadac4861869b7f32e43c6ec162d9977980e361a61592a5ac0a1"
        ],
        "data": []
      },
      {
        "from_address": "0x49d36570d4e46f48e99674bd3fcc84644ddd6b96f7c741b1562b82f9e004dc7",
        "keys": [
          "0x99cd8bde557814842a3121e8ddfd433a539b8c9f14bf31ebf108d12e6196e9",
          "0x54f15de9ef0eaa1f52412a39219b6a17ee9b3d38d6fad210784f1fa7b027fbd",
          "0x1000"
        ],
        "data": [
          "0x193168a90800",
          "0x0"
        ]
      }
    ],
    "execution_status": "SUCCEEDED",
    "finality_status": "ACCEPTED_ON_L2",
    "block_hash": "0x5ce5af63e454ddab242b0c8d3a604021043a609981889ba38795ec70b8cf6f7",
    "block_number": 13,
    "execution_resources": {
      "steps": 7879,
      "memory_holes": 182,
      "range_check_builtin_applications": 275,
      "pedersen_builtin_applications": 19,
      "poseidon_builtin_applications": 5,
      "ec_op_builtin_applications": 3,
      "data_availability": {
        "l1_gas": 0,
        "l1_data_gas": 256
      }
    }
  },
  "contract": "lib.cairo",
  "function": "transfer_ownership"
}
------------------ End Invoking transfer_ownership -------------------
------------------- Calling get_owner ------------------------
{
  "resp": [
    "0x56c93bf54e3eadac4861869b7f32e43c6ec162d9977980e361a61592a5ac0a1"
  ],
  "contract": "lib.cairo",
  "function": "get_owner"
}
------------------- End calling get_owner --------------------
------------------- Calling get_owner ------------------------
{
  "resp": [
    "0x56c93bf54e3eadac4861869b7f32e43c6ec162d9977980e361a61592a5ac0a1"
  ],
  "contract": "lib.cairo",
  "function": "get_owner"
}
------------------- End calling get_owner --------------------

### 2024.09.21

<!-- Content_END -->
