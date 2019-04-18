---
title: wallet api
type: source
order: 6
---

# wallet api overview

```python
from pyeoskit import wallet
```

### wallet.create

Creates a new wallet with the given name

```python
wallet.create('mywallet')
```

If the creation is successful, it returns the wallet's password string. If the creation fails, for example, the wallet already exists, etc., it returns an empty string.

### wallet.open

Opens an existing wallet of the given name

```python
wallet.open('mywallet')
```

### wallet.unlock

Unlocks a wallet with the given name and password

```python
psw = 'password return from wallet.create'
wallet.unlock('mywallet', psw)
```

### wallet.lock

Locks an existing wallet of the given name

```python
wallet.lock('mywallet')
```

### wallet.set_timeout

Sets wallet auto lock timeout (in seconds)

```python
wallet.set_timeout(60)
```

### wallet.save

Saves wallet

```python
wallet.save('mywallet')
```

### wallet.set_dir

Sets the directory where the wallet is located

### wallet.list_keys

Lists all key pairs across all wallets

```python
wallet.list_keys('mywallet', psw)
```

### wallet.list_wallets()

Lists all wallets in the directory

### wallet.get_public_keys

Lists all public keys across all opened wallets

```python
wallet.get_public_keys()
```

### wallet.lock_all

Locks all opened wallets

```python
wallet.lock_all()
```

### wallet.import_key

Imports a private key to the wallet of the given name

```python
wallet.import_key('mywallet', priv_key)
```

### sign_transaction

Signs a transaction

