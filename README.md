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
|-----|-----|-----|:-----|-----|
|K=25|600 MB | 1.8 GB |	只支持测试网
|K=32|101.4 GB | 332 GB	| 主网可用
|K=33|208.8 GB | 589 GB	| 主网可用
|K=34|429.8 GB | 1177 GB | 主网可用
|K=35|884.1 GB | 2355 GB |	主网可用

## 集群搭建

## 命令行参数

## 常见问题



www.kuangjiwan.com/news/news-2883.html
技术绿皮书 https://www.chia.net/assets/ChiaGreenPaper.pdf
Chia挖矿教程 https://www.kuangjiwan.com/news/news-2882.html
Chia(奇亚)常见问题解答 https://www.kuangjiwan.com/news/news-2884.html
Chia(奇亚)命令行参数 https://www.kuangjiwan.com/news/news-2886.html
Chia(奇亚)plot文件规格大小 https://www.kuangjiwan.com/news/news-2887.html
Chia减半计划表 https://www.kuangjiwan.com/news/news-2889.html
Chia多机集群教程 https://www.kuangjiwan.com/news/news-2891.htm