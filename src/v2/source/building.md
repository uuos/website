---
title: Building
type: source
order: 2
---

# Building UUOS

## Downloading Source Code

```bash
git clone https://www.github.com/learnforpractice/eos
cd eos
git submodule update --init --recursive
```

## Installing dependencies (Ubuntu)

```
sudo apt-get install libleveldb-dev
sudo apt-get install libreadline-dev
```

## Installing dependencies (macOS)

```
brew install leveldb
brew install readline
```

## Building

```bash
./eosio_build.py
```
