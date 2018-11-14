---
title: UUOS
type: source
order: 0
---

　　Python is popular among many developers because of its simple use and high development efficiency. Althogh the most important thing about programming is the idea behind it, the expression of thought is also important. Python is such a programming language which has strong expression ability. A famous adage about Python says: Life is short, use Python. We can understand that Python is an efficient development language. Python has wide applications in the fields of scientific calculation, network programming, artificial intelligence, etc.

　　Ethereum smart contract function has made Ethereum popular, and it even drove the bull market of the previous blockchain. Ethereum smart contract function enabled Ethereum to take the second place in the blockchain market. Smart contracts will be an essential function for blockchain projects. But smart contract itself has many problems, the most obvious problems are the performance and ease of use. The performance and ease of use of Ethereum's solidity smart contract language are not desirable. The design of smart contract language is not simple, but it's a problem that must be solved in the blockchain world. Since Python is so good, why not use Python directly as a smart contract language? In fact, early Ethereum had already recognized this problem. The earliest Ethereum smart contract language serpent is a Python-like language that was later replaced by solidity. Now Ethereum is developing vyper language, which is also a Python-like language. A description of vyper on github is: Pythonic Smart Contract Language for the EVM. And it has more than 2000 start on github. Why does Ethereum focus on the development of Python-like languages with great passion? The most fundamental reason is that Python is easy to use and has a large user base. Another reason is that the founder of Ethereum, Vitalik Buterin, is a die-hard fan of Python. In fact, Python has also contributed to Ethereum. The earliest Ethereum version was developed by Python, followed by versions of C++ and Go.

　　Here is a question: Since Python is so easy to use, why does Ethereum not directly use Python as a smart contract language? Because it's not suitable. Ethereum smart contract is based on the GAS payment model, which requires accurate calculation of the CPU occupied by the code and the cost of the code to operate the storage space. Ethereum calls it GAS. The native Python interpreter has a lot of code, which is a lot more complicated than a simple EVM. It is difficult to calculate GAS.

　　Then Let us talk about why Python can be used as a smart contract programming language for Eos. Eos is brought to us by Daniel Larimer and his development team. Because Eos's TS is free, and it calculates the running time of the CPU when running a smart contract. It doesn't take the time and effort to calculate the GAS of each line of code like Ethereum, making it possible to use Python as the development language of smart contracts. It Removes a major obstacle to make Python become a smart contract language. Thanks to Daniel Larimer, the hard-working developers saw a light.

　　NOW to return to the performance of Python. In fact, today developers are more concerned about software development efficiency and maintenance cost. As for performance, it is fully able to meet the need with current CPU's computing power in most cases. You might need to worry about performance ten to twenty years ago, but now, you really don’t need it in most use cases. In addition, the pareto principle is also applicable to program. That is, 20% code takes up 80% run time. To Python,  20% bytecode takes up 80% runtime. And many Python's key modules are implemented in C, in fact 80% of Python program running time is running C code other than interpreting bytecode most of the time. That's why Python's performance won't be too bad in most cases, even without optimization. In fact, Python's list, dict and other key modules are running at a fast speed that is similar to C/C++. To be honest, there is a big difference between being able to use Python and being good at using Python. Of course, high-performance blockchain projects still have high requirements for the performance of smart contract languages. From the test result, cpython's running time is three times faster than wasm's binaryen, in the same data level with wasm's wabt mode. It also shows that the speed of python smart contract can meet the requirements.
		
　　At last, this is Zen of Python.
1. Beautiful is better than ugly.
2. Explicit is better than implicit.
3. Simple is better than complex.
4. Complex is better than complicated.
5. Flat is better than nested.
6. Sparse is better than dense.
7. Readability counts.
8. Special cases aren't special enough to break the rules.
9. Although practicality beats purity.
10. Errors should never pass silently.
11. Unless explicitly silenced.
12. In the face of ambiguity, refuse the temptation to guess.
13. There should be one-- and preferably only one --obvious way to do it.
14. Although that way may not be obvious at first unless you're Dutch.
15. Now is better than never.
16. Although never is often better than right now.
17. If the implementation is hard to explain, it's a bad idea.
18. If the implementation is easy to explain, it may be a good idea.
19. Namespaces are one honking great idea -- let's do more of those!
