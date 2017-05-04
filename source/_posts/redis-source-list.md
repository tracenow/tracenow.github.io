title: Redis源码剖析-源码结构分析  
categories: redis 
tags: [redis, source]
---

# Redis 4.0源码阅读列表

## 一、基础数据结构
* 内存分配 [zmalloc.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/zmalloc.h)、[zmalloc.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/zmalloc.c)、[sdsalloc.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sdsalloc.h)
* 简单动态字符串 [sds.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sds.h)、[sds.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sds.c)
* 双端链表 [adlist.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/adlist.h)、[adlist.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/adlist.c)
* 字典 [dict.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/dict.h)、[dict.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/dict.c)
* 跳跃表 [server.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/server.h)（zskiplist以及zskiplistNode结构）、[t_zset.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_zset.c)(zsl开头的函数)
* 整数集合 [intset.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/intset.h)、[intset.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/intset.c)
* 压缩列表 [ziplist.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ziplist.h)、[ziplist.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ziplist.c)
* 压缩字典 [zipmap.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/zipmap.h)、[zipmap.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/zipmap.c)
* 快速链表 [quicklist.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/quicklist.h、[quicklist.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/quicklist.c)
* 基数统计 [hyperloglog.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/hyperloglog.c)(hllhdr结构, hll 开头的函数)
* geohash [geohash.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geohash.h)、[geohash.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geohash.c)

## 二、Redis数据类型
* 对象系统 [object.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/object.c)
* 字符串键 [t_string.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_string.c)
* 列表建 [t_list.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_list.c)
* 哈希键 [t_hash.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_hash.c)
* 集合键 [t_set.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_set.c)
* 有序集合键 [t_zset.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/t_zset.c)(除zsl开头的所有函数)
* HyperLogLog键 [hyperloglog.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/hyperloglog.c)(pf开头的函数)
* 地理位置 [geo.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geo.h)、[geo.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geo.c)

## 三、Redis数据库
* 数据库实现 [db.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/db.c)
* 通知功能 [notify.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/notify.c)
* RDB持久化 [rdb.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rdb.h)、[rdb.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rdb.c)
* AOF持久化 [aof.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/aof.c)

## 四、客户端/服务端
* 事件处理模块 [ae.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae.h)、[ae.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae.c)、[ae_epoll.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae_epoll.c)、[ae_evport.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae_evport.c)、[ae_kqueue.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae_kqueue.c)、[ae_select.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/ae_select.c)
* 网路链接库 [anet.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/anet.h)、[anet.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/anet.c)、[networking.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/networking.c)
* 服务器端 [server.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/server.h)、[server.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/server.c)
* 客户端 [redis-cli.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/redis-cli.c)

## 五、分布式Redis
* 复制功能 [replication.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/replication.c)
* Redis哨兵 [sentinel.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sentinel.c)
* Redis集群 [cluster.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/cluster.h)、[cluster.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/cluster.c)

## 六、独立功能模块
* 发布和订阅 [pubsub.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/pubsub.c)
* 事务 [multi.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/multi.c)

## 七、测试
* 内存检测 [memtest.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/memtest.c)
* redis性能测试 [redis_benchmark.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/redis_benchmark.c)
* 更新日志检查 [redis_check_aof.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/redis_check_aof.c)
* 本地数据库检查 [redis_check_rdb.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/redis_check_rdb.c)
* C风格的小型测试框架 [testhelp.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/testhelp.c)

## 八、工具类
* 二进制位操作命令 [bitops.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/bitops.c)
* 调试 [debug.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/debug.c)
* 高低位转换 [endianconv.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/endianconv.h)、[endianconv.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/endianconv.c)(适配不同系统)
* 辅助于命令的提示信息 [help.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/help.h)
* 压缩算法 [lzf.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/lzf.h)、[lzf_c.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/lzf_c.c)、[lzf_d.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/lzf_d.c)、[lzfP.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/lzfP.h)
* 随机数 [rand.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rand.h)、[rand.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rand.c)
* 版本发布 [release.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/release.c)
* sha加密算法 [sha1.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sha1.h)、[sha1.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sha1.c)
* 通用工具类 [util.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/util.h)、[util.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/util.c)
* 循环冗余校验 [crc16.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/crc16.c)、[crc64.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/crc64.h)、[crc64.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/crc64.c)
* SORT命令 [sort.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sort.c)
* 伪随机函数 [siphash.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/siphash.c)
* 进程信息操作 [setproctitle.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/setproctitle.c)
* geo工具类 [geohash_helper.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geohash_helper.h)、[geohash_helper.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/geohash_helper.c)

## 九、封装类
* 后台线程I/O [bio.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/bio.h)、[bio.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/bio.c)
* 延迟类 [latency.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/latency.h)、[latency.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/latency.c)
* 排序算法类 [pqsort.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/pqsort.h)、[pqsort.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/pqsort.c)
* Redis定义的I/O类 [rio.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rio.h)、[rio.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/rio.c)
* 同步Socket和文件I/O操作 [syncio.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/syncio.c)

## 十、其他
* 微线图 [sparkline.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sparkline.h)、[sparkline.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/sparkline.c)
* 慢日志 [slowlog.h](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/slowlog.h)、[slowlog.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/slowlog.c)
* 脚本 [scripting.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/scripting.c)
* 过期机制 [expire.c](https://github.com/tracenow/redis-4.0-annotation/blob/master/src/expire.c)