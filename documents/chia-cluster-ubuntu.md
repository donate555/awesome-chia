# Chia 挖矿集群搭建

## 集群架构

## 安装Chia
```sh
sudo apt-get update
sudo apt-get upgrade -y

# Checkout the source and install
git clone https://github.com/Chia-Network/chia-blockchain.git -b latest
cd chia-blockchain

sh install.sh

. ./activate
```
官方的文档还需要安装`chia-blockchain-gui`，这个在Linux系统上不需要，我编译也一直未通过。

## 创建钱包、备份私钥
#### 初始化
```sh
chia init
```

#### 创建钱包
```sh
# 创建钱包
chia keys generate

# 查看钱包
chia keys show
```

## 启动主节点
```sh
chia start all
```
这里有很多参数可以选择，选择`all`就是启动全节点，直接启动全节点就行。
- all:
- node:
- harvester:
- farmer:
- farmer-no-wallet:
- farmer-only:
- timelord:
- timelord-only:
- timelord-launcher-only:
- wallet:
- wallet-only:
- introducer:
- simulator:

查看同步进度：
```sh
chia show -s
```

查看日志：
```sh
cat ~/.chia/mainnet/log
```

## 导入钱包
主节点启动后，在其他从机上，先安装好`chia-blockchain`，然后导入钱包，保证从机是在同一个钱包下完成P盘过程。
```sh
chia keys add <mnemonic>
```

## 启动Plotman开始P盘
在主机或从机上启动Plotman开始P盘，主机和从机都是可以P盘的，只是主机上多了一个全节点。
```sh
git clone https://github.com/ericaltendorf/plotman.git
```
先切换到`chia-blockchain`，执行`. ./activate`，初始化好Python虚拟环境，然后再切换回`plotman`目录，执行`python3 plotman.py -h`，就能看到`plotman`的各种操作了。

注意，第一次执行的时候，需要安装2个python的依赖库:
```sh
pip3 install psutil
pip3 install texttable
```

然后就可以执行`python3 plotman.py plot`开始发P盘任务了。