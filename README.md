# Awesome Chia

## 资源汇总
- [Chia官网](https://www.chia.net)
- [区块浏览器](https://www.chiaexplorer.com)
- [技术绿皮书](https://www.chia.net/assets/ChiaGreenPaper.pdf)
- [Chia Github代码仓库](https://github.com/Chia-Network)
- [Chia blockchain python implementation](https://github.com/Chia-Network/chia-blockchain): 包含Chia任务调度、所有的协议和钱包，Python通过`from chiapos import DiskPlotter`调用最核心的算法模块`chiapos`
- [Chia blockchain GUI](https://github.com/Chia-Network/chia-blockchain-gui): Chia 挖矿管理客户端，管理节点、钱包、Plots、Farm等，基于TypeScript、React和Electron
- [chiapos](https://github.com/Chia-Network/chiapos): Chia 核心算法处证明库，使用C++编写，底层的P盘逻辑、证明、验证都在这个里面，高手可以研究一下能否使用GPU来P

## Plot文件规格大小
Plot是Chia网络中的最小存储单元，主网上线后，只支持K=32的P盘文件(plots files)进行挖矿，不同的文件格式意味着单个P盘文件的大小不同，K越大意味着P盘文件越大。通常情况下K=32已经完全满足主网的挖矿需求，但是在实际应用过程中，不同规格的P盘文件搭配使用更有利于最大限度的存满一个硬盘。

|规格|最终P盘文件大小|P盘临时文件大小|备注|
|:-----|:-----|:-----|:-----|-----|
|K=25|600 MB | 1.8 GB |	只支持测试网
|K=32|101.4 GB | 332 GB	| 主网可用
|K=33|208.8 GB | 589 GB	| 主网可用
|K=34|429.8 GB | 1177 GB | 主网可用
|K=35|884.1 GB | 2355 GB |	主网可用

## 集群搭建
#### 安装Chia
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

#### 初始化Chia
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

#### 启动主节点
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

#### 导入钱包
主节点启动后，在其他从机上，先安装好`chia-blockchain`，然后导入钱包，保证从机是在同一个钱包下完成P盘过程。
```sh
chia keys add <mnemonic>
```

#### 启动Plotman开始P盘
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

## 命令行参数
#### 初始化
```sh
chia init
```

#### 开启服务

#### P盘

#### 校验P盘文件