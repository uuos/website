---
title: eos api
type: source
order: 5
---

# eos api overview

```python
from pyeoskit import eosapi
```

### eosapi.create_key

Create a new password

```python
#In Eos, each account can have multiple keys, and owner key and active key are frequently used.
#Create a owner key
eosapi.create_key()
#Return value
{
    'public':owner_public_key
    'private':owner_private_key
}
#Create an active key. Ditto.
```

### eosapi.create_account

Create a new account. Before creating new account, determine that owner key's and active key's private keys have been imported into the wallet, and then create an account with the corresponding public key.

```python
#Import wallet first
#Execute the command first: wallet.import_key(wallet_name,private_key)
eosapi.create_account('eosio',account_name,owner_public_key,active_public_key)
```

[For more wallet api, see here](walletapi.html)

### eosapi.get_info

Returns an object containing various details about the blockchain.

```python
eosapi.get_info()
```

### eosapi.get_block

Returns an object containing various details about a specific block on the blockchain.

```python
eosapi.get_block(block_num_or_id)
```

### eosapi.get_block_header_state

Returns producer's information

```python
eosapi.get_block_header_state(block_num_or_id)
```

### eosapi.get_account

Returns account's information

```python
eosapi.get_account(account_name)
```

### eosapi.get_abi

Returns contract's information

```python
eosapi.get_abi(account_name)
```

### eosapi.get_code

Returns smart contract's code

```python
eosapi.get_code(account_name)
```

### eosapi.get_raw_code_and_abi

Returns smart contract's abi

```python
eosapi.get_raw_code_and_abi(account_name)
```

### eosapi.get_table_rows

Returns smart contract's data information

??Get data from database, such as currency balance, 合约代码要求存的中间状态等等

??"code" is contract account，"scope" is set in contract (similar to mysql's database)，table is also set in contract (similar to mysql's table)

```python
code="eosio"
scope="eosio"
table=account_name
json="true"
lower_bound=0
upper_bound=4
limit=2

eosapi.get_table_rows(scope,code,table,json,lower_bound,upper_bound,limit)
```

### eosapi.abi_json_to_bin

Serialize json to hexadecimal codes

Hexadecimal codes received is used for "push_transaction" data field.

```python
code = 'currency'
action = 'transfer'
args = {"from":"initb","to":"initc","quantity":9999}
eosapi.abi_json_to_bin(code,action,args)

#Return value
{
  "binargs": "000000008093dd74000000000094dd74e803000000000000",
  "required_scope": [],
  "required_auth": []
}
```

### eosapi.abi_bin_to_json

Serialize hexadecimal codes to json

```python
code = 'currency'
action = 'transfer'
binargs = '000000008093dd74000000000094dd74e803000000000000'
eosapi.abi_json_to_bin(code,action,binargs)
```

### eosapi.get_currency_balance

Get currency balance information (If there isn't any smart contract, you may not obtain the balance information)

```python
eosapi.get_currency_balance(code='eosio',account=account_name,symbol='SYS')
```

### eosapi.get_required_keys

Returns the required keys needed to sign a transaction

```python
available_keys=[
    "EOS5ySgzeHp9G7TqNDGpyzaCtahAeRcTvPRPJbFey5CmySL3vKYgE",
    "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
    "EOS6gXwNz2SKUNAZcyjzVvg6KdNgA1bSuVzCr8c5yWkGij52JKx8V"
    ]
    
transaction={
        "actions": [
            {
                "account": "eosio.token",
                "authorization": [
                    {
                        "actor": "eosio",
                        "permission": "active"
                    }
                ],
                "data": "0000000000ea305500000000487a2b9d102700000000000004454f53000000001163726561746564206279206e6f70726f6d",
                "name": "transfer"
            }
        ],
        "context_free_actions": [
        ],
        "context_free_data": [
        ],
        "delay_sec": 0,
        "expiration": "2018-11-28T17:20:30.500",
        "max_kcpu_usage": 0,
        "max_net_usage_words": 0,
        "ref_block_num": 245107,
        "ref_block_prefix": 801303063,
        "signatures": [
        ]
    }
}

eosapi.get_required_keys(available_keys,transaction)

#Return value
{
    "required_keys": [
        "EOS6gXwNz2SKUNAZcyjzVvg6KdNgA1bSuVzCr8c5yWkGij52JKx8V"
    ]
}
```

### eosapi.get_currency_stats

Get token's information

```python
eosapi.get_currency_stats(code='eosio',accountname='your account',symbol='SYS')
```

### eosapi.get_producers

??Get producers' node

```python
eosapi.get_producers(json,lower_bound)
```

### eosapi.push_block

Produce a block

```python
eosapi.push_block(block)
```

### eosapi.push_transaction

Send transaction. This method expects a transaction in JSON format and will attempt to apply it to the blockchain.

```python
signed_transaction={
    "ref_block_num":"101",
    "ref_block_prefix":"4159312339",
    "expiration":"2017-09-25T06:28:49",
    "scope":["initb","initc"],
    "actions":[{
        "code":"currency",
        "type":"transfer",
        "recipients":["initb","initc"],
        "authorization":[{
            "account":"initb","permission":"active"
            }],
        "data":"000000000041934b000000008041934be803000000000000"
        }],
    "signatures":[],"authorizations":[]
    }

eosapi.push_transaction(sign_transaction)
```

### eosapi.push_transactions

This method pushes multiple transactions at a time to achieve multiple transactions at the same time.

```python
Operation is as eosapi.push_transaction
```

### eosapi.get_actions

Returns account's Actions list

pos and offset mean： Get the "offset" Actions from the first "pos" record

```python
eosapi.get_actions(account_name,pos,offset)
```

### eosapi.get_transaction

Returns transaction details

```python
eosapi.get_transaction(id)
```

### eosapi.get_key_accounts

Returns the account corresponding to the public key

```python
eosapi.get_key_accounts(public_key)
```

### eosapi.gen_transaction

Create a transaction unsighed

```python
reference_block_id = eosapi.get_info().last_irreversible_block_id
eosapi.gen_transaction([['hello', 'sayhello', b'', {'hello':'active'}]], 60, reference_block_id)
```

