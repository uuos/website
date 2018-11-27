---
title: 智能合约创建
type: source_en
order: 3
---

#创建你的第一个Python智能合约

###运行 UUOS

打开终端, 进入 [PROJECT_DIR]/build/program, 执行下面命令

```
./UUOS/UUOS --manual-gen-block --debug -i
```

UUOS会在您第一次启动时为您创建一个测试钱包，位置在 data-dir/mywallet.wallet, 控制台会打印钱包密码,如下所示:

```
wallet password: PW5JWE5g6RZ7Fyr2kmCphDqZo4uivdeGpUpndgFZ52rsduhtf9PRJ
```

由于仅用于测试，密码将保存到 data-dir / data.pkl，因此下次启动UUOS进行测试时，UUOS会为您解锁钱包。

同时,UUOS会将三个私钥导入钱包，这对测试非常有用。

```
'5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3',
'5JEcwbckBCdmji5j8ZoMHLEUS8TqQiqBG1DRx1X9DN124GUok9s',
'5JbDP55GXN7MLcNYKCnJtfKi9aD2HvHAdY7g8m67zFTAFkY1uBB'
```

注意,不要在真实帐户中使用这些私钥，否则您将丢失帐户中的所有加密属性。

此外,UUOS会为你创建4个重要的账户

```
eosio.bios, eosio.msig, eosio.system, eosio.token
```

并在测试网上面发布它们的智能合约。

尽管上述步骤在现实世界中永远不会发生，但它确实为测试智能合约提供了极大的便利。从而节省了大量宝贵的时间，提高了开发效率。

### 使用sketch生成源代码

在UUOS控制台中执行以下命令，

```
sketch.build('hello', 'helloworld', 'py')
```

它将在当前目录下创建一个helloworld目录，hello作为测试账户名，在该目录下生成以下三个文件：

```
helloworld.py
helloworld.abi
t.py
```

其中，helloworld.py是Python智能合约源代码，helloworld.abi是智能合约的ABI（应用程序二进制接口）文件，t.py包含用于测试智能合约的代码。

此外，sketch还可以为您创建一个wasm智能合约项目，只需在UUOS控制台中输入以下命令，测试过程与Python智能合约没有区别。

```
sketch.build('helloworld', 'helloworld', 'cpp')
```

### 测试


现在运行你的helloworld智能合约。在UUOS控制台输入或复制以下命令：

```python
from helloworld import t
t.test()
```

你会看到控制台有绿色的字输出，如下所示：

```
3289633ms thread-1   mpeoslib.cpp:63               print                ] hello,world
```

恭喜，你已经成功运行第一个Python智能合约。

现在您可以打开helloworld.py进行编码。 一旦完成，只需再次运行t.test（），无需运行其他命令来发布您的测试智能合约，如果在运行t.test（）期间helloworld.py已发生改变，智能合约会自动重新发布到测试网。您还可以在t.py中编辑测试代码来测试智能合约。 一旦完成，只需再次运行t.test（），就不需要运行reload（t），UUOS会为你施魔法。 这也适用于在测试中添加新功能的情况。

在 programs/UUOS/contracts中有很多例子。其中一些仍在开发中，如果示例抛出异常，那么它可能还没有完成。选择您感兴趣的示例并根据需要使用它。
