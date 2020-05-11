# Redis

[官网地址](http://www.redis.cn/commands/bitop.html)

## 数据类型

### 五大数据类型

#### string

```bash
localhost:6379> set key1 123 #设置一个key
OK
localhost:6379> get key1 #获取一个key
"123"
localhost:6379> setnx key2 456 #如果key2不存在设置key2的值
(integer) 1
localhost:6379> get key2
"456"
localhost:6379> setex key3 12 789 #如果key3存在，设置过期时间，设置值
OK
localhost:6379> get key3
"789"
localhost:6379> append key3 1011 #在key3的后面拼接数据
(integer) 4
localhost:6379> get key3
"1011"
localhost:6379> incr key3 #递增key3
(integer) 1012
localhost:6379> decr key3 #递减key3
(integer) 1011
localhost:6379> incrby key3 10 #步增key3
(integer) 1021
localhost:6379> decrby key3 10 #步减key3
(integer) 1011
localhost:6379> mget key1 key2 key3 #批量获取key值
1) "123"
2) "456"
3) "1011"
localhost:6379> setrange key3 0 789 #从0位置设置key3的值
(integer) 4
localhost:6379> get key3
"7891"
localhost:6379> getrange key3 2 3 #获取范围内key3的值
"91"
localhost:6379> strlen key3 #获取key3的长度
(integer) 4
#setbit 和 bitcount 连用可以计算 用户 A 上线了多少天，用户 B 上线了多少天 
#单个 Redis 实例最小储存 2.5 亿个 key
localhost:6379> setbit key4 1 1
(integer) 0
localhost:6379> setbit key4 2 1
(integer) 0
localhost:6379> setbit key4 3 1
localhost:6379> bitcount key4
(integer) 3
```



#### list

#### set

#### zset

#### hash

### 三种特殊数据类型

#### geospatial

 

#### hyperloglog



#### bitmaps



## 事务



## Jedis



## springboot 整合



## redis.conf



## redis持久化

redis的持久化操作分为两种一种是rdb快照根据保存规则保存快照，存储key-value,另一种是aof，采用日志的形式记录每次插入的操作，追加到文件中，也是有自己的追加规则，对比这两个持久化操作可以从恢复数据量的大小，数据的完整性和一致性上回答。redis只做缓存的话，开启rdb就行，要做持久化操作两个都要开启主要是以aof为主，rdb做数据备份。

关闭rdb 关闭保存策略就可以了



## redis发布订阅



## redis主从复制



## redis缓存穿透和雪崩



