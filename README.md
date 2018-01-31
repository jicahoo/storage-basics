# storage-basics

# Disk tech
* PCIe: https://en.wikipedia.org/wiki/PCI_Express
* https://www.krollontrack.com/blog/2017/05/04/future-sata-sas/ SATA, SAS, NVMe是同一层次的概念，都是Disk的访问协议。SAS更适于SSD, NVMe应该是专门为SSD开发的访问协议。
* SAS在物理层兼容SATA标准。 SAS用在企业级
* SAS https://www.snia.org/sites/default/education/tutorials/2007/spring/networking/SAS-Overview.pdf
* 读了SCSI的wikipeda: SCSI是一个标准集，这个标准集目标是连接**计算机系统和外围设备**。标准包含了命令集，协议，电子和光学接口。主要用于硬盘。类比，以太网技术的目标是连接计算机。TCP/IP的目标是连接网络。

# PATA vs SATA
* 为什么Serial的，反而性能高？https://en.wikipedia.org/wiki/Serial_communication vs https://en.wikipedia.org/wiki/Parallel_communication

# RAID技术
* 基本概念和手段：数据冗余（镜像，校验码），并发读写（条带化-stripe).
* RAID 0 使用条带化， RAID 1使用镜像，RAID 5使用条带化和校验码，RAID 10是 RAID 1 + RAID 0, 镜像上的条带化。
* https://www.thegeekstuff.com/2010/08/raid-levels-tutorial

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
* Amazon DynamoDB. 既支持文档，又支持键值。

## 分布式文档数据库
* CouchDB
* MongoDB

## 分布式表格系统 ?
* Google Big Table, Google Megastore
* Windows Azure Storage

## 专用分布式存储系统
* 搜索：Elastic Search
* 图(Graph): Neo4j
