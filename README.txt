[root@demo ~]# redis-cli 
127.0.0.1:6379> AUTH your_password
OK
127.0.0.1:6379> PING
PONG
127.0.0.1:6379> ECHO "Hello World"
"Hello World"
127.0.0.1:6379> SET name yaochenzhi
OK
127.0.0.1:6379> GET name
"yaochenzhi"
127.0.0.1:6379> SET myname yaochenzhi hername "the lovely"
(error) ERR syntax error
127.0.0.1:6379> MSET myname yaochenzhi hername "the lovely"
OK
127.0.0.1:6379> GET myname
"yaochenzhi"
127.0.0.1:6379> GET hername
"the lovely"
127.0.0.1:6379> MGET myname hername
1) "yaochenzhi"
2) "the lovely"
127.0.0.1:6379> MSET key1 hello key2 world
OK
127.0.0.1:6379> APPEND key1 " world"
(integer) 11
127.0.0.1:6379> GET key1
"hello world"
127.0.0.1:6379> SET age 18
OK
127.0.0.1:6379> GET age
"18"
127.0.0.1:6379> INCR age
(integer) 19
127.0.0.1:6379> GET age
"19"
127.0.0.1:6379> DECR age
(integer) 18
127.0.0.1:6379> FLUSHALL
OK
127.0.0.1:6379> LPUSH mylist world
(integer) 1
127.0.0.1:6379> LPUSH mylist Hello
(integer) 2
127.0.0.1:6379> RPUSH mylist !
(integer) 3
127.0.0.1:6379> RPUSH mylist "My name is yaochenzhi !"
(integer) 4
127.0.0.1:6379> LRANGE 0 -1
(error) ERR wrong number of arguments for 'lrange' command
127.0.0.1:6379> LRANGE mylist 0 -1
1) "Hello"
2) "world"
3) "!"
4) "My name is yaochenzhi !"
127.0.0.1:6379> LRANGE mylist 0 2
1) "Hello"
2) "world"
3) "!"
127.0.0.1:6379> FLUSHALL
OK
127.0.0.1:6379> LPUSH namelist Ma
(integer) 1
127.0.0.1:6379> LPUSH namelist Jack
(integer) 2
127.0.0.1:6379> LPUSH namelist Jackie
(integer) 3
127.0.0.1:6379> LRANGE namelist 0 -1
1) "Jackie"
2) "Jack"
3) "Ma"
127.0.0.1:6379> LRANGE namelist 0 2
1) "Jackie"
2) "Jack"
3) "Ma"
127.0.0.1:6379> LRANGE namelist 0 1
1) "Jackie"
2) "Jack"
127.0.0.1:6379> LLEN namelist
(integer) 3
127.0.0.1:6379> LINSERT namelist AFTER Jackie Chan
(integer) 4
127.0.0.1:6379> LRANGE namelist 0 -1
1) "Jackie"
2) "Chan"
3) "Jack"
4) "Ma"
127.0.0.1:6379> RPUSH namelist !
(integer) 5
127.0.0.1:6379> LRANGE namelist 0 -1
1) "Jackie"
2) "Chan"
3) "Jack"
4) "Ma"
5) "!"
127.0.0.1:6379> RPOP namelist
"!"
127.0.0.1:6379> LRANGE namelist 0 -1
1) "Jackie"
2) "Chan"
3) "Jack"
4) "Ma"
127.0.0.1:6379> FLUSHALL
OK
127.0.0.1:6379> SADD cars Ford
(integer) 1
127.0.0.1:6379> SADD cars Honda
(integer) 1
127.0.0.1:6379> SADD cars BMW
(integer) 1
127.0.0.1:6379> SISMEMBER cars
(error) ERR wrong number of arguments for 'sismember' command
127.0.0.1:6379> SISMEMBER cars Ford
(integer) 1
127.0.0.1:6379> SISMEMBER cars not
(integer) 0
127.0.0.1:6379> SISMEMBER cars
(error) ERR wrong number of arguments for 'sismember' command
127.0.0.1:6379> SMEMBERS cars
1) "Honda"
2) "Ford"
3) "BMW"
127.0.0.1:6379> SCARD cars
(integer) 3
127.0.0.1:6379> SMOVE cars mycars Ford
(integer) 1
127.0.0.1:6379> SMEMBERS mycars
1) "Ford"
127.0.0.1:6379> SMEMBERS cars
1) "Honda"
2) "BMW"
127.0.0.1:6379> SREM cars BMW
(integer) 1
127.0.0.1:6379> SMEMBERS cars
1) "Honda"
127.0.0.1:6379> ZADD users 1979 "Creator"
(integer) 1
127.0.0.1:6379> ZADD users 1980 "Worker"
(integer) 1
127.0.0.1:6379> ZADD users 1990 "Keeper"
(integer) 1
127.0.0.1:6379> ZRANK users Keeper
(integer) 2
127.0.0.1:6379> ZRANK users Creator
(integer) 0
127.0.0.1:6379> ZRANGE users 0 -1
1) "Creator"
2) "Worker"
3) "Keeper"
127.0.0.1:6379> ZINCRBY users 1 Keeper
"1991"
127.0.0.1:6379> ZINCRBY users 10 Keeper
"2001"
127.0.0.1:6379> FLUSHALL
127.0.0.1:6379> HSET user:jack name "Jack Ma"
(integer) 1
127.0.0.1:6379> HSET user:jack email "jack@gmail.com"
(integer) 1
127.0.0.1:6379> HGET user:jack
(error) ERR wrong number of arguments for 'hget' command
127.0.0.1:6379> HGET user:jack email
"jack@gmail.com"
127.0.0.1:6379> HGETALL user:jack
1) "name"
2) "Jack Ma"
3) "email"
4) "jack@gmail.com"
127.0.0.1:6379> HMSET user:john name "Jone Doe" email "jdoe@yahoo.com"
OK
127.0.0.1:6379> HGETALL user:john
1) "name"
2) "Jone Doe"
3) "email"
4) "jdoe@yahoo.com"
127.0.0.1:6379> HVAL user:john
(error) ERR unknown command 'HVAL'
127.0.0.1:6379> HKEYS user:john
1) "name"
2) "email"
127.0.0.1:6379> HVALS user:john
1) "Jone Doe"
2) "jdoe@yahoo.com"
127.0.0.1:6379> HSET user:john age 20
(integer) 1
127.0.0.1:6379> HINCRBY user:john age 1
(integer) 21
127.0.0.1:6379> HGETALL user:john
1) "name"
2) "Jone Doe"
3) "email"
4) "jdoe@yahoo.com"
5) "age"
6) "21"
127.0.0.1:6379> HDEL user:john age
(integer) 1
127.0.0.1:6379> HGETALL user:john
1) "name"
2) "Jone Doe"
3) "email"
4) "jdoe@yahoo.com"
127.0.0.1:6379> HLEN user:john
(integer) 2
127.0.0.1:6379> EXISTS name
(integer) 0
127.0.0.1:6379> SET name yachenzhi
OK
127.0.0.1:6379> SET name yaochenzhi
OK
127.0.0.1:6379> EXISTS name
(integer) 1
127.0.0.1:6379> GET name
"yaochenzhi"
127.0.0.1:6379> 
127.0.0.1:6379> SAVE
OK

PERSISTENCE
CP /ETC/REDIS.CONF{,DEFAULT};
VIM /ETC/REDIS.CONF
