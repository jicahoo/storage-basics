# storage-basics

# terms:
* DUDL: Data unavailable, data loss
# Disk tech
* PCIe: https://en.wikipedia.org/wiki/PCI_Express
* https://www.krollontrack.com/blog/2017/05/04/future-sata-sas/ SATA, SAS, NVMe是同一层次的概念，都是Disk的访问协议。SAS更适于SSD, NVMe应该是专门为SSD开发的访问协议。
* SAS在物理层兼容SATA标准。 SAS用在企业级
* SAS https://www.snia.org/sites/default/education/tutorials/2007/spring/networking/SAS-Overview.pdf
* 读了SCSI的wikipeda: SCSI是一个标准集，这个标准集目标是连接**计算机系统和外围设备**。标准包含了命令集，协议，电子和光学接口。主要用于硬盘。类比，以太网技术的目标是连接计算机。TCP/IP的目标是连接网络。

# PATA vs SATA
* 为什么Serial的，反而性能高？https://en.wikipedia.org/wiki/Serial_communication vs https://en.wikipedia.org/wiki/Parallel_communication
# NVMe
* https://searchstorage.techtarget.com/definition/NVMe-over-FC-Nonvolatile-Memory-Express-over-Fibre-Channel
* https://www.ibm.com/downloads/cas/MLAEO6R8 (Very good book on NVMe) NVMe over Fibre Channel For dummies
* https://zhuanlan.zhihu.com/p/71932654 理解NVMe的内部实现原理，这一篇就够了
* https://nvmexpress.org/
* SPDK (Storage Performance Development Kit) https://github.com/spdk/spdk
* 详谈NVMe和NVMe-oF架构和知识点 https://blog.csdn.net/btb5e6nsu1g511eg5xeg/article/details/96398907
* 在linux系统中配置NVMe over TCP https://www.cnblogs.com/JamesLi/p/11399054.html
* NVMe over Fabrics 技术特征 https://www.cnblogs.com/JamesLi/p/11511082.html

# Flash Memory
* 杂谈闪存二：NOR和NAND Flash https://zhuanlan.zhihu.com/p/26745577
* 杂说闪存一：关公战秦琼之 UFS VS NVMe https://zhuanlan.zhihu.com/p/26652622
* 杂谈闪存三：FTL https://zhuanlan.zhihu.com/p/26944064
* 杂说闪存四：闪存硬盘接口大比拼 https://zhuanlan.zhihu.com/p/27068849

# SSD
* The Top 20 Things to Know About SSD
https://www.seagate.com/files/www-content/product-content/pulsar-fam/_cross-product/en-us/docs/ssd-faq-tp612-2-1103us.pdf#:~:text=The%20Top%2020%20Things%20to%20Know%20About%20SSD,Ang%20Mo%20Kio%20Avenue%205%2C%20Singapore%20569877%2C%2065-6485-3888
# SCM
* https://blocksandfiles.com/2018/11/28/2019-the-year-of-storage-class-memory/
* https://blog.netapp.com/storage-class-memory-what-is-next-in-enterprise-storage/
* https://researcher.watson.ibm.com/researcher/files/us-gwburr/Almaden_SCM_overview_Jan2013.pdf

# NVRAM
# NVM
# Persistent Memory

# Flash Memory
* Flash memory summit: https://www.flashmemorysummit.com/English/Collaterals/Proceedings/2018/20180806_PreConC_Webb.pdf

# 3D XPoint
* https://en.wikipedia.org/wiki/3D_XPoint

# Standard
* SNIA
* JEDEC

# 概念区分
* SSD中，SATA、m2、PCIE和NVME各有什么意义呢？ - 知乎用户的回答 - 知乎 https://www.zhihu.com/question/48972075/answer/253574912 https://www.userbenchmark.com/Faq/What-s-the-difference-between-SATA-PCIe-and-NVMe/105
* SSD中，SATA、m2、PCIE和NVME各有什么意义呢？ - 褚道长的回答 - 知乎 https://www.zhihu.com/question/48972075/answer/521468195
```text
作者：褚道长
链接：https://www.zhihu.com/question/48972075/answer/521468195
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

1. 物理接口M.2 , U.2 , AIC, NGFF 这些属于物理接口。像 M.2 可以是 SATA SSD 也可以是 NVMe（PCIe） SSD。金手指上有一个 SATA/PCIe 的选择信号，来区分两者。很多笔记本的M.2 接口也是同时支持两种类型的盘的。 M.2 , 主要用在 笔记本上，优点是体积小，缺点是散热不好。U.2,主要用在 数据中心或者一些企业级用户，对热插拔需求高的地方。优点热插拔，散热也不错。一般主要是pcie ssd(也有sas ssd)，受限于接口，最多只能是 pcie 4laneAIC，企业，行业用户用的比较多。通常会支持pcie 4lane/8lane，带宽上限更高

2. 高速信号协议 SAS，SATA，PCIe 这三个是同一个层面上的，模拟串行高速接口。SAS 对扩容比较友好，也支持双控双活。接上SAS RAID 卡，一般在阵列上用的比较多。SATA 对热插拔很友好，早先台式机装机市场的 SSD基本上都是SATA的，现在的 机械硬盘也是SATA接口居多。但速率上最高只能到 6Gb/s，上限 550MB/s左右，现在已经慢慢被pcie取代。PCIe 支持速率更高，也离CPU最近。很多设备 如 网卡，显卡 也都走pcie接口，当然也有SSD。现在比较主流的是PCIe 3.0,8Gb/s 看起来好像也没比 SATA 高多少，但是 PCIe 支持多个LANE，每个LANE都是 8Gb/s，这样性能就倍数增加了。目前，SSD主流的是 PCIe 3.0x4 lane，性能可以做到 3500MB/s 左右。

3. 传输层协议SCSI，ATA，NVMe 都属于这一层。主要是定义命令集，数字逻辑层。SCSI 命令集 历史悠久，应用也很广泛。U盘，SAS 盘，还有手机上 UFS 之类很多设备都走的这个命令集。ATA 则只是跑在SATA 协议上NVMe 协议是有特意为 NAND 进行优化。相比于上面两者，效率更高。主要是跑在 PCIe 上的。当然，也有NVMe-MI，NVMe-of之类的。是个很好的传输层协议。

4. 总结M.2,U.2,AIC 是物理规格，像是 公路，铁路。PCIe，SATA，SAS 是 模拟高速接口，像是 县道，省道，高速这样。速率上限不同SCSI，ATA，NVMe 是传输层协议，命令集。就是跑在路上面的小车，只是有 跑车 和 面包车 之分。所以，如果要买SSD的话，不是只看 M.2就完事了 ，得分清了 是 SATA 的，还是 NVMe 的，看看主板支持的到底是哪种。否则，买回来的东西可能会用不了！原创手打，能力有限，欢迎大家指错。
```

# RAID技术
* 基本概念和手段：数据冗余（镜像，校验码），并发读写（条带化-stripe).
* RAID 0 使用条带化， RAID 1使用镜像，RAID 5使用条带化和校验码，RAID 10是 RAID 1 + RAID 0, 镜像上的条带化。
* https://www.thegeekstuff.com/2010/08/raid-levels-tutorial

# 开源存储技术
* http://www.enterprisestorageforum.com/storage-technology/open-source-storage-64-applications.html

# 数据保护
* 复制(replicate)
* RAID
* Erasure Coding.

## 数据保护参考
* https://www.snia.org/sites/default/files/SDC15_presentations/datacenter_infra/Shenoy_The_Pros_and_Cons_of_Erasure_v3-rev.pdf
* https://ceph.com/planet/erasure-coding-in-ceph/
* 一个Veeam (数据保护公司）的人写的，关于数据保护技术Erasure Coding. https://www.virtualtothecore.com/en/erasure-coding-best-data-protection-scaling/

## 发展趋势的一些判断
* 单个磁盘的容量越来越大，但是读写速度没有跟上磁盘容量的上涨，而RAID提出是针对当时的磁盘大小和读写速度的，所以，RAID技术在大磁盘时代，不一定完全适用，会出现一些瓶颈。所以有些新技术来解决这些问题。需要更多的数据支持,权威资料支持。

## 文件系统
* 一些有关文件系统的精炼的tips: http://www.scs.stanford.edu/14wi-cs140/notes/file_systems-print.pdf


## 分布式存储
一个大致的分类，不一定完全准确。

### 分布式文件系统
* GFS, HDFS
* GlusterFS, GPFS
* Islion OneFS
* 图片存储专用系统：Taobao File System, Facebook Haystack.

## 分布式对象存储
* Openstack swift
* Ceph
 * https://www.youtube.com/watch?v=OyH1C0C4HzM
 * http://docs.ceph.com/docs/master/start/intro/
 * RADOS: https://ceph.com/wp-content/uploads/2016/08/weil-rados-pdsw07.pdf
 * CRUSH: https://ceph.com/wp-content/uploads/2016/08/weil-crush-sc06.pdf
* Hedvig (文档数据库)
* EMC ECS

### 分布式块存储
* Ceph, ScaleIO, vSAN

### 分布式键值存储
* Amazon Dynamo: 
  * http://web.engr.illinois.edu/~pbg/courses/cs598fa10/readings/dynamo.pdf
* Redis, Memcache

## 分布式数据库
* MySQL Sharding
* Microsoft SQL Azure
* Google Spanner
* Greenplum
* Cassandra (P2P)

## 分布式文档数据库
* CouchDB
* MongoDB
* Amazon DynamoDB. 既支持文档，又支持键值。

## 分布式表格系统 ?
* Google Big Table, Google Megastore
* Windows Azure Storage

## 专用分布式存储系统
* 搜索：Elastic Search
* 图(Graph): Neo4j
