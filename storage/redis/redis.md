# go语言中Redis使用参考

## redis 介绍

Redis 是一个开源（BSD许可）的，内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件。
作为内存NoSQL数据库，redis也支持持久化，redis中的数据以**key—value**的形式存储，**所有的命令
都是原子的**

## redis中的数据结构

### key

可以使用任意二进制序列作为key，空字符串也可以作为有效的key。

* 	key的长度不要太长，不要超过1024字节，这样既消耗内存，又要开销长时间计算

*	key的命名尽量可读


### string

存储任意二进制值，值的长度不能超过512M。

*	支持原子操作

*	支持超时机制

### list

**linked list**， 相当于双向链表


### hash

实现hash结构

### set

无序、不重复的string集合

### order-set

有序、不重复的string集合

### bitmap

其实是字符串，每个字符串最大512MB，所以每个bitmap最大4Gbit

### hyperloglog

估算一个集合的基数（不同元素的个数）， 于set不同，hyperloglog
并不存储元素的值，因而hyperloglog占用的内存不会因为元素个数的
增长而增长，而是占用固定的内存（12KB），就可以估算元素个数长达
2^64的集合的基数，估算误差在一定的范围内

## go语言使用redis

下面介绍go语言中使用*github.com/gomodule/redigo/redis*包访问redis

1.  初始化reids连接池

    ````go
    //RedisHost为redis服务器的地址，如: "127.0.0.1:9980"
    //RedisMaxIdleConn为连接池中最大空闲连接数，如：1024
    RedisPool = redis.NewPool(func() (redis.Conn, error) { return redis.Dial("tcp", RedisHost) }, RedisMaxIdleConn)
    ````

2.  从连接池中获得reids连接

    ````go
    conn := RedisPool.Get()
	defer conn.Close()
    ````

3.  向redis发送命令

    ````go
    conn.Send(...)
    conn.Do(...)
    ````

4.  接收redis响应

    ````
    conn.Receive()
    ````

## 参考

1.	[https://www.tutorialspoint.com/redis/redis_quick_guide.htm](https://www.tutorialspoint.com/redis/redis_quick_guide.htm)
1.  [https://godoc.org/github.com/gomodule/redigo/redis](https://godoc.org/github.com/gomodule/redigo/redis)


