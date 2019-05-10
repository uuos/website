---
title: eos api
type: source
order: 5
---

# eos api overview

Import eosapi

```python
from pyeoskit import eosapi
```

### eosapi.create_key

Create a new password

```python
eosapi.create_key()

Return value

{
    'public':'EOS8Gbv4v7oLnWC3pQwg4tJHbv7cQFuxuDnHAFKrbiVtmKx6VHBwK',
    'private':'5J6NzFGPDJDFzaiRzezeJwvNHomY91oaDYnQT8kraKUPm6y1bZ5'
}
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
eosapi.get_account('eosio')
```

### eosapi.get_abi

Returns contract's information

```python
eosapi.get_abi('eosio.token')
```

### eosapi.get_code

Returns smart contract's code

```python
eosapi.get_code('eosio.token')
```

### eosapi.get_raw_code_and_abi

Returns smart contract's binary code and abi

```python
eosapi.get_raw_code_and_abi('eosio.token')
```

### eosapi.get_table_rows

```python
eosapi.get_table_rows(True, 'eosio.token', 'EOS', 'stat', 'EOS', '', '', 1)
```

```python
{
    "rows": [
        {
            "supply": "1044451904.2438 EOS",
            "max_supply": "10000000000.0000 EOS",
            "issuer": "eosio"
        }
    ],
    "more": false
}
```

### eosapi.abi_json_to_bin

Serialize json to hexadecimal codes

```python
args = {'from':'inita', 'to':'initb', 'quantity':'1.0000 EOS', 'memo':'hello,world'}
eosapi.abi_json_to_bin('eosio.token', 'transfer', args)
```

Returns

```python
{
    "binargs": "000000000093dd74000000008093dd74102700000000000004454f53000000000b68656c6c6f2c776f726c64"
}
```

### eosapi.abi_bin_to_json

Serialize hexadecimal codes to json

```python
binargs = "000000000093dd74000000008093dd74102700000000000004454f53000000000b68656c6c6f2c776f726c64"
eosapi.abi_bin_to_json('eosio.token', 'transfer', binargs)
```

```python
{
    "args": {
        "from": "inita",
        "to": "initb",
        "quantity": "1.0000 EOS",
        "memo": "hello,world"
    }
}
```

### eosapi.get_currency_balance

Get currency balance information

```python
eosapi.get_currency_balance('eosio.token', 'eosio.saving' ,'EOS')
```

### eosapi.get_required_keys

Returns the required keys needed to sign a transaction

### eosapi.get_currency_stats

Get token's information

```python
eosapi.get_currency_stats('eosio.token', 'EOS')
```

```python
{
    "EOS": {
        "supply": "1010853656.0071 EOS",
        "max_supply": "10000000000.0000 EOS",
        "issuer": "eosio"
    }
}
```
### eosapi.get_producers

Get block producers' information

```python
{
    "rows": [
        {
            "owner": "eoshuobipool",
            "total_votes": "912780250023381248.00000000000000000",
            "producer_key": "EOS5XKswW26cR5VQeDGwgNb5aixv1AMcKkdDNrC59KzNSBfnH6TR7",
            "is_active": 1,
            "url": "http://eoshuobipool.com",
            "unpaid_blocks": 2508,
            "last_claim_time": "2019-05-09T00:29:02.000",
            "location": 0
        },
        {
            "owner": "starteosiobp",
            "total_votes": "888420867709618944.00000000000000000",
            "producer_key": "EOS4wZZXm994byKANLuwHD6tV3R3Mu3ktc41aSVXCBaGnXJZJ4pwF",
            "is_active": 1,
            "url": "https://www.starteos.io",
            "unpaid_blocks": 5415,
            "last_claim_time": "2019-05-08T15:58:09.000",
            "location": 156
        }
    ],
    "total_producer_vote_weight": "47230651279257329664.00000000000000000",
    "more": "eoslaomaocom"
}
```

```python
eosapi.get_producers(True, "", 2)
```

### eosapi.push_block

### eosapi.push_transaction

Send transaction

```python
from pyeoskit import eosapi
from pyeoskit import wallet

#wallet.unlock('testwallet', 'YOUR WALLET PASSWORD')

args = {"from": 'helloworld12',
        "to": 'hello',
        "quantity": '0.0001 EOS',
        "memo": 'hello,world'
}
action = ['eosio.token', 'transfer', args, {'helloworld12':'active'}]
reference_block_id = eosapi.get_info().last_irreversible_block_id
trx = eosapi.gen_transaction([action], 120, reference_block_id)
public_keys = ['EOS4uFSpSqLovSD7cB7XgAkGxnAja3zASnQwuMjoQwP3cwyhdNFdX']

info = eosapi.get_info()
trx = wallet.sign_transaction(trx, public_keys, info.chain_id)
trx = eosapi.pack_transaction(trx, 0)
eosapi.push_transaction(trx)
```

### eosapi.push_transactions

Pushes multiple transactions

```python
from pyeoskit import db
from pyeoskit import eosapi
from pyeoskit import wallet

#wallet.unlock('YOUR WALLET NAME', 'YOUR WALLET PASSWORD')

args1 = {"from": 'helloworld12',
        "to": 'eosio',
        "quantity": '0.0001 EOS',
        "memo": 'hello,world'
}
action1 = ['eosio.token', 'transfer', args1, {'helloworld12':'active'}]

args2 = {"from": 'helloworld12',
        "to": 'eosio.token',
        "quantity": '0.0001 EOS',
        "memo": 'hello,world'
}
action2 = ['eosio.token', 'transfer', args2, {'helloworld12':'active'}]

r = eosapi.push_transactions([[action1, action2]])
```

### eosapi.get_actions

Returns account's Actions list

pos and offset mean： Get the "offset" Actions from the first "pos" record

```python
eosapi.get_actions('eosio.token', 0, 1)
```

```python
{
    "actions": [],
    "last_irreversible_block": 1001186
}
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

