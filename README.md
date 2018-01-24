# storage-basics

# Disk tech
* PCIe: https://en.wikipedia.org/wiki/PCI_Express
* https://www.krollontrack.com/blog/2017/05/04/future-sata-sas/ SATA, SAS, NVMe是同一层次的概念，都是Disk的访问协议。SAS更适于SSD, NVMe应该是专门为SSD开发的访问协议。

# 数据保护
* 复制(replicate)
* RAID
* Erasure Coding.

## 数据保护参考
* https://www.snia.org/sites/default/files/SDC15_presentations/datacenter_infra/Shenoy_The_Pros_and_Cons_of_Erasure_v3-rev.pdf
* https://ceph.com/planet/erasure-coding-in-ceph/

## 发展趋势的一些判断
* 单个磁盘的容量越来越大，但是读写速度没有跟上磁盘容量的上涨，而RAID提出是针对当时的磁盘大小和读写速度的，所以，RAID技术在大磁盘时代，不一定完全适用，会出现一些瓶颈。所以有些新技术来解决这些问题。需要更多的数据支持,权威资料支持。
