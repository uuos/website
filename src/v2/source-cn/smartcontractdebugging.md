---
title: 智能合约调试
type: source_en
order: 4
---

# 智能合约调试

Python智能合约支持源代码级调试。开发人员可以使用pydevd Eclipse插件在Eclipse IDE中调试他们的智能合约，同时支持其他IDE，如Visual Studio Code，请搜索在线资源了解如何远程调试Python源代码。对于pydevd，这里有一个参考[manual_adv_remote_debugger](http://www.pydev.org/manual_adv_remote_debugger.html)。环境设置成功后，在UUOS控制台中执行以下命令启用调试。

```
debug.enable()
```

在Eclipse中，在python智能合约源代码中设置断点。如果您的Python智能合约源代码没有放在 UUOS/contracts 目录中，则需要执行以下命令来指定源代码目录，并且智能合约源代码文件必须位于具有相同名称的目录下。

```
 sys.path.append(<folder where source code directory in>)
```

将智能合约部署到testnet，以UUOS/contracts中的hello智能合约为例，在hello.py中设置断点，并执行以下命令来调用hello.py

```
from hello import t
t.test()
```

当执行到断点所在行的代码时，智能合约会停止继续运行。


如果要禁用调试，请执行以下命令。

```
debug.disable()
```

![Smart Contract Debugging](https://raw.githubusercontent.com/learnforpractice/pyeos/master/programs/pyeos/debugging/debugging.png)

