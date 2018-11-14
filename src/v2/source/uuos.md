---
title: UUOS
type: source
order: 0
---

　　Python因其简单易用，开发效率高而深受广大开发者的喜爱和推崇。虽说编程最重要的是背后的思想，但是思想的表达也是非常的重要的。Python正是这种有强大表达能力的语言。Python有句名言：Life is short, use Python.中文版是：人生苦短，我用Python。可以从一个侧面来了解Python是一个高效的开发语言。在科学计算，网络编程，人工智能等等领域，Python有着广泛的应用。

　　以太坊智能合约功能让以太坊火了起来，甚至带动了上一波的区块链的牛市。以太坊也凭借它的智能合约功能坐上了区块链市场的第二把交椅的位置。智能合约将会是以后区块链项目的必备的功能。但是智能合约本身却也有许多的问题，最明显的就是性能和易用性问题。以太坊的solidity智能合约语言在性能和易用性上都不尽如人意。智能合约语言的设计并不是简单的事情，但是却又是区块链世界必须解决的问题。既然Python这么好用，为什么不直接用Python作为智能合约语言呢？其实，早期的以太坊就早就已经认识到了这个问题。最早的以太坊智能合约语言serpent就是一种类Python的语言，后面逐渐被solidity所替代。现在以太坊又在开发vyper语言，也是一种类Python语言。github上对它的描述是：Pythonic Smart Contract Language for the EVM。在github上已经2000多start了。为什么以太坊在类Python语言的开发上情有独忠呢，最根本的原因还是因为Python好用，用户群体广泛。还有一个原因是以太坊的创始人Vitalik Buterin是一个Python的死忠粉。实际上Python还为以太坊作出了功不可没的贡献，最早期的以太坊版本就是用Python开发的，后面才有C++和Go的版本。

　　这里就提出来一个问题：既然Python这么好用，为什么以太坊不直接把python作为智能合约语言？原因是不适合。Ethereum的智能合约是基于GAS付费模型的，需要精确的计算代码所占的CPU和代码操作存储空间所需的花费，以太坊称之为GAS。而原生的Python解释器有众多的代码，相对于简单的EVM虚拟机来说，要复杂很多，要计算GAS比较困难。

　　下面来谈谈Python为什么能作为Eos的智能合约编程语言。Eos是Daniel Larimer以及他的开发团队为我们带来了的，因为Eos的TS是零费用的，运行智能合约的时候计算的是CPU的运行时间，不用像Ethereum那样去费时费力的计算每一行代码的GAS，使得用Python作为智能合约的开发语言成为可能。为Python成为智能合约语言移除了一个大阻碍。所以感谢Daniel Larimer吧，苦哈哈的开发者们看到了一丝曙光。

　　再来说说Python的性能问题。其实在今天这个世界里，开发者更关注的是软件的开发效率和维护成本。至于性能，在大多数情况下，以现在CPU的计算能力，是完全能够满足需求的。如果在十几二十年前，你可能还需要为了性能而斤斤计较，但是现在，大多数应用场景下，真的不用了。并且在Python代码不满足性能要求时，完全有很方便的方法来对Python代码进行优化以几倍几十倍的提高代码的性能。另外，二八定律也同样适用于程序的运行。也就是说，20%的代码占用了80%的运行时间。具体到Python语言，20%的bytecode占用了80%的运行时间，并且由于Python的关键模块很多都是通过C来实现的，所以实际上80%的Python程序运行时间又是大部分时间里都在运行除解释bytecode以外的C代码。这也就是即使不采用优化手段，Python的性能在大多数情况下不会太差的原因。事实上，Python的list,dict等等关键模块的运行速度已经和C/C++写的代码没有多大的差别了。但是，有句实话还是得说：会用Python和用好Python还是有很大的差别的。当然，高性能的区块链项目对智能合约语言的性能还是有比较高的要求的，从测试的情况来看，cpython的运行速度比wasm的binaryen运行方式会快3倍以上。和wasm的wabt运行模式处于同一个数据级。这也说明了python智能合约的运行速度是能够满足要求的。

最后，祭出Python之禅(Zen of Python)作为本篇的结束

Zen of Python(Python之禅)

1. Beautiful is better than ugly.

优美胜于丑陋（Python 以编写优美的代码为目标）

2. Explicit is better than implicit.

明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）

3. Simple is better than complex.

简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）

4. Complex is better than complicated.

复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）

5. Flat is better than nested.

扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）

6. Sparse is better than dense.

间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）

7. Readability counts.

可读性很重要（优美的代码是可读的）

8. Special cases aren't special enough to break the rules.

9. Although practicality beats purity.

即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上）

10. Errors should never pass silently.

11. Unless explicitly silenced.

不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写except:pass风格的代码）

12. In the face of ambiguity, refuse the temptation to guess.

当存在多种可能，不要尝试去猜测

13. There should be one-- and preferably only one --obvious way to do it.

而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）

14. Although that way may not be obvious at first unless you're Dutch.

虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido）

15. Now is better than never.

16. Although never is often better than right now.

做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）

17. If the implementation is hard to explain, it's a bad idea.

18. If the implementation is easy to explain, it may be a good idea.

如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）

19. Namespaces are one honking great idea -- let's do more of those!

命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）



参考链接：

http://blog.csdn.net/gzlaiyonghao/article/details/2151918
