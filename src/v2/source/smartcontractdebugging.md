---
title: Smart Contract Debugging
type: source
order: 4
---

# Smart Contract Debugging

Python smart contract supports source level debugging. Developers can debug their smart contract in Eclipse IDE with pydevd Eclipse pluging, and other IDEs may also be supported, such as Visual Studio Code. Please search for online resources to find out how to debug Python source remotely. As for pydevd, there is a reference from here [manual_adv_remote_debugger](http://www.pydev.org/manual_adv_remote_debugger.html). Once the environment is set up successfully, run the following command in UUOS console to enable debugging

```
debug.enable()
```

Set breakpoint at your python smart contract source code in Eclipse. If your Python smart contract source code is not placed in UUOS/contracts directory, then you need to run the following code to specify your source code directory and your smart contract source code file must be under a directory with the same name.

```
 sys.path.append(<folder where source code directory in>)
```

Deploy your smart contract to the testnet. Take hello contract in UUOS/contracts for example. Set breakpoint at hello.py, and run the following code to call hello.py

```
from hello import t
t.test()
```

Smart contract execution will be stopped when the code at the line of breakpoint is being executed.


To disable debugging, run the following code

```
debug.disable()
```

![Smart Contract Debugging](https://raw.githubusercontent.com/learnforpractice/pyeos/master/programs/pyeos/debugging/debugging.png)

