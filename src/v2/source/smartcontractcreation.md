---
title: Smart Contract Creation
type: source
order: 3
---

# Creating Your First Python Smart Contract

### Running UUOS

Open a terminal, cd to [PROJECT_DIR]/build/program, run the following command

```
./UUOS/UUOS --manual-gen-block --debug -i
```

If it's the first time you start UUOS, UUOS will create a testing wallet for you, which is placed in data-dir/mywallet.wallet, and then console will print the wallet password as below:

```
wallet password: PW5JWE5g6RZ7Fyr2kmCphDqZo4uivdeGpUpndgFZ52rsduhtf9PRJ
```

Since it's for testing only, password will save to data-dir/data.pkl. So next time you start UUOS for testing, UUOS will unlock wallet for you.

Also UUOS will import three private keys to the wallet, which is useful for testing.

```
'5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3',
'5JEcwbckBCdmji5j8ZoMHLEUS8TqQiqBG1DRx1X9DN124GUok9s',
'5JbDP55GXN7MLcNYKCnJtfKi9aD2HvHAdY7g8m67zFTAFkY1uBB'
```

Keep in mind that these private keys should never be used in real account, otherwise you will lose all of your crypto property in the account.

Besides, UUOS will create four important accounts for you:

```
eosio.bios, eosio.msig, eosio.system, eosio.token
```

and publish their smart contract on testnet. 

Although the above steps will never happen in the real world, but it really provides a great convenience for testing smart contract. Thus save a lot of your precious time and make the development more efficient.

### Generating source code with sketch

Run the following command in UUOS console,

```
sketch.build('hello', 'helloworld', 'py')
```

That will create a helloworld directory under your current directory with hello as the testing account name. There are three files generated in the directory:

```
helloworld.py
helloworld.abi
t.py
```

Which helloworld.py is the Python smart contract source code, helloworld.abi is the ABI(Application Binary Interface) file for smart contract, t.py contains code for testing smart contract.

In addition, sketch can also create a wasm smart contract project for you, just type the following code in UUOS console, and the testing process has no difference with Python smart contract.

```
sketch.build('helloworld', 'helloworld', 'cpp')
```

### Testing


Now it's time to run your helloworld smart contract. Type or copy the following commands to the UUOS console:

```python
from helloworld import t
t.test()
```

You will see the following output on console in green words:

```
3289633ms thread-1   mpeoslib.cpp:63               print                ] hello,world
```

Congratulations, you have successfully run your first Python smart contract.

Now you can open helloworld.py for coding. Once it's done, just run t.test() again. 
There is no need to run other commands to publish your testing smart contract. The smart contract will be automatically
republished to the testnet if it's been changed during the running of t.test(). You can also edit the testing code in t.py for testing your smart contract. Once it's done, just run t.test() again. There is no need to run reload(t). UUOS will do the magic for you. That also works at the situation of adding a new function in test. 

There are a lot of examples in programs/UUOS/contracts. Some of them are still in development, if the example throws exception, then it's probably not done yet. Pick up an example you interest in and play with it as you want. 
