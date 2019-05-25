# Mock Jedis

Mock Jedis is a library for mocking out [Jedis](https://github.com/xetorthio/jedis) clients.
It's useful for testing your code without actually having a live redis server up.
Currently, fp-mock-jedis supports pipelining and all the basic Jedis commands, but if you find missing 
functionality you're welcome to submit a pull request.

This version was forked from [50onRed](https://github.com/50onRed/mock-jedis) version of mock-jedis,
which looks like it is no longer maintained. Package was changed to avoid collisions if maintenance is
continued on that project.

## Compile
with gradle (preferred method):
```shell
gradle build
```

## Adding fp-mock-jedis to your project

Add it as a dependency to your project.

Here's a sample gradle script that will pull fp-mock-jedis 2.6.0.0 from maven-central
```gradle
buildscript {
    repositories {
        mavenCentral()
    }
}

apply plugin: 'java'

dependencies {
  testCompile 'com.freedompop:fp-mock-jedis:2.6.0.0'
}
```

Sample maven dependency definition:
```xml
<dependency>
    <groupId>com.freedompop</groupId>
    <artifactId>fp-mock-jedis</artifactId>
    <version>2.6.0.0</version>
    <type>jar</type>
    <scope>test</scope>
</dependency>
```

## Using fp-mock-jedis
```java
Jedis j = new MockJedis("test");
j.set("test", "123");
assertEquals("123", j.get("test"));
```

## Supported Commands
Currently the following commands are supported by fp-mock-jedis
 - KEYS: DEL DUMP EXISTS EXPIRE EXPIREAT KEYS PERSIST PEXPIRE PEXPIREAT PTTL RANDOMKEY RENAME RENAMENX RESTORE TTL TYPE
 - STRINGS: APPEND DECR DECRBY GET GETSET INCR INCRBY INCRBYFLOAT MGET MSET MSETNX PSETEX SET SETEX SETNX STRLEN
 - HASHES: HDEL HEXISTS HGET HGETALL HINCRBY HINCRBYFLOAT HKEYS HLEN HMGET HMSET HSET HSETNX HVALS
 - LISTS: LLEN LPOP LPUSH
 - SETS: SADD SCARD SDIFF SDIFFSTORE SINTER SINTERSTORE SISMEMBER SMEMBERS SMOVE SPOP SRANDMEMBER SREM SUNION SUNIONSTORE
 - CONNECTIONS: ECHO PING SELECT QUIT
 - SERVER: DBSIZE FLUSHALL FLUSHDB
 - PIPELINES

## Unsupported Things
 - All commands not listed above
