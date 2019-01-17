---
title: 构建
type: source_cn
order: 2
---

# 构建UUOS

## 下载源代码

```bash
git clone https://www.github.com/learnforpractice/pyeos
cd UUOS
git submodule update --init --recursive
```

## 安装依赖 (Ubuntu)

```
sudo apt-get install libleveldb-dev
sudo apt-get install libreadline-dev
```

## 安装依赖 (macOS)

```
brew install leveldb
brew install readline
```

## 构建

```bash
./eosio_build.sh
```
