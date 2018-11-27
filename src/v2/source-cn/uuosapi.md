---
title: UUOS api 接口
type: source_en
order: 5
---

# UUOS api 接口概述

#### eosapi.get_info
```python
info = eosapi.get_info()
info
```

```javascript
{
    "server_version": "00000000",
    "head_block_num": 127,
    "last_irreversible_block_num": 126,
    "head_block_id": "0000007fbd1ff82f29668dfa89d927a0510c657cce292c033496ccaacf04c12a",
    "head_block_time": "2018-05-06T07:57:44",
    "head_block_producer": "eosio"
}
```

```python
info.head_block_time
```
```
'2017-09-23T15:16:18'
```

```python
info.head_block_num
```

```
18624
```

#### wallet.create

UUOS会在您第一次启动时为您创建一个测试钱包，但您也可以创建其他钱包 wit wallet.create API

```python
psw = wallet.create('mywallet2')
psw
```

```
'PW5JCWXaGkA15s6th6AWCabHewuGASAtrUJjTWoL1Ybx6sG9QzrSb'
```
你现在可以看到你的钱包了。 mywallet后面的*表示钱包已解锁。

```
wallet.list_wallets()
```

```
['mywallet *']
```
#### wallet.open wallet.unlock

```
wallet.open('mywallet2')
wallet.unlock('mywallet2','PW5JCWXaGkA15s6th6AWCabHewuGASAtrUJjTWoL1Ybx6sG9QzrSb')
```

#### wallet.import_key
让我们导入inita的私钥。 请参阅[设置钱包和导入帐户密钥](https://github.com/learnforpractice/pyeos#setting-up-a-wallet-and-importing-account-key)获取更多信息.

```
wallet.import_key('mywallet2','5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3')
```

#### eosapi.create_key

创建 owner key

```python
eosapi.create_key()
```

```
{'public': 'EOS61MgZLN7Frbc2J7giU7JdYjy2TqnfWFjZuLXvpHJoKzWAj7Nst', 'private': '5JEcwbckBCdmji5j8ZoMHLEUS8TqQiqBG1DRx1X9DN124GUok9s'}
```

创建 active key

```python
eosapi.create_key()
```

```
{'public': 'EOS5JuNfuZPATy8oPz9KMZV2asKf9m8fb2bSzftvhW55FKQFakzFL', 'private': '5JbDP55GXN7MLcNYKCnJtfKi9aD2HvHAdY7g8m67zFTAFkY1uBB'}
```

导入 owner key

```python
wallet.import_key('mywallet2','5JEcwbckBCdmji5j8ZoMHLEUS8TqQiqBG1DRx1X9DN124GUok9s')
```

导入 active key

```python
wallet.import_key('mywallet2','5JbDP55GXN7MLcNYKCnJtfKi9aD2HvHAdY7g8m67zFTAFkY1uBB')
```

#### eosapi.create_account
现在创建账户, 你之前创建的 key1 和 key2 是公钥。

```
key1 = 'EOS61MgZLN7Frbc2J7giU7JdYjy2TqnfWFjZuLXvpHJoKzWAj7Nst'
key2 = 'EOS5JuNfuZPATy8oPz9KMZV2asKf9m8fb2bSzftvhW55FKQFakzFL'
eosapi.create_account('eosio', 'currency',key1,key2)

```

```javascript
{
    "transaction_id": "f6c43148dfac54105031fbaf966958d36309dd94e665c506eb2769e43febedba",
    "processed": {
        "status": "executed",
        "kcpu_usage": 100,
        "net_usage_words": 44,
        "id": "f6c43148dfac54105031fbaf966958d36309dd94e665c506eb2769e43febedba",
        "action_traces": [
            {
                "receiver": "eosio",
                "context_free": false,
                "cpu_usage": 0,
                "act": {
                    "account": "eosio",
                    "name": "newaccount",
                    "authorization": [
                        {
                            "actor": "eosio",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "creator": "eosio",
                        "name": "currency",
                        "owner": {
                            "threshold": 1,
                            "keys": [
                                {
                                    "key": "EOS61MgZLN7Frbc2J7giU7JdYjy2TqnfWFjZuLXvpHJoKzWAj7Nst",
                                    "weight": 1
                                }
                            ],
                            "accounts": []
                        },
                        "active": {
                            "threshold": 1,
                            "keys": [
                                {
                                    "key": "EOS5JuNfuZPATy8oPz9KMZV2asKf9m8fb2bSzftvhW55FKQFakzFL",
                                    "weight": 1
                                }
                            ],
                            "accounts": []
                        },
                        "recovery": {
                            "threshold": 1,
                            "keys": [],
                            "accounts": [
                                {
                                    "permission": {
                                        "actor": "eosio",
                                        "permission": "active"
                                    },
                                    "weight": 1
                                }
                            ]
                        }
                    },
                    "hex_data": "0000000000ea30550000001e4d75af4601000000010002934a4748562795f31685de7b0112c3f4428255d42aa8ea420701c29542ede46501000001000000010002376f7109de7a6cf12a8d6c713fa7f4d4df8a9e08ecee47e9001583c7b8fcc9750100000100000000010000000000ea305500000000a8ed32320100"
                },
                "console": "",
                "data_access": [
                    {
                        "type": "write",
                        "code": "eosio",
                        "scope": "eosio.auth",
                        "sequence": 39
                    }
                ],
                "_profiling_us": 38
            }
        ],
        "deferred_transaction_requests": [],
        "read_locks": [],
        "write_locks": [
            {
                "account": "eosio",
                "scope": "eosio.auth"
            }
        ],
        "cpu_usage": 102400,
        "net_usage": 352,
        "packed_trx_digest": "373a3125c5728b7feb7a4b5d04330e9de64e5f393123e660ff210ca558864c99",
        "region_id": 0,
        "cycle_index": 1,
        "shard_index": 0,
        "_profiling_us": 66,
        "_setup_profiling_us": 127
    },
    "cost_time": 608
}
```
#### eosapi.produce_block

这个命令是用来你测试智能合约时生成区块的。

```
eosapi.produce_block()
```

#### eosapi.get_transaction

我们现在可以测试get_transaction，用create_account命令输出的transcation id替换'f6c43148dfac54105031fbaf966958d36309dd94e665c506eb2769e43febedba'，您会注意到输出与上面create_account命令的输出相同。

```python
r = eosapi.get_transaction('f6c43148dfac54105031fbaf966958d36309dd94e665c506eb2769e43febedba')
r
r.transaction.signatures
r.transaction.packed_trx
```

#### eosapi.get_account

```python
info = eosapi.get_account('eosio')
info
```
```
{
    "account_name": "eosio",
    "permissions": [
        {
            "perm_name": "active",
            "parent": "owner",
            "required_auth": {
                "threshold": 1,
                "keys": [
                    {
                        "key": "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
                        "weight": 1
                    }
                ],
                "accounts": []
            }
        },
        {
            "perm_name": "owner",
            "parent": "",
            "required_auth": {
                "threshold": 1,
                "keys": [
                    {
                        "key": "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
                        "weight": 1
                    }
                ],
                "accounts": []
            }
        }
    ]
}
```

#### eosapi.set_contract
将Python智能合约发布到区块链

```python
r = eosapi.set_contract('hello','../../programs/pyeos/contracts/hello/hello.py','../../contracts/hello/hello.abi',1)
r
```

#### eosapi.get_table

...

#### eosapi.push_action

...

