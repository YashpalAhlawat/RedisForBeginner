# Redis for Begginers

It is a simple repo for Redis related commands and theory.

## Simple commands

### Connetion relevent Commands

- **AUTH**:- Authenticate the Server.

>Request for authentication in password protected redis server.If password matches the password present in configuration file then it will send OK status, Otherwise throw error to clent and client need to try new password.

- **ECHO**:- Echo the given string.

```console
>redis-cli
>echo "Hello World"
```

- **PING**:- Ping server.

>Used to test if connection is still active

- **QUIT**:- Close the connection.

- **SELECT**:- Change selected database for current connection.

> By defualt 0 db is selected

- **SWAPDB**:- Swap the two DBs.

```console
>swapdb 0 1
```

### Command Related to String

- **Exist**:- if a key already exist in db. Syntax **Exist [Key]**

```console
> Exist dbname
```

>if dbname key exits it will return 1. otherwise 0.

- **Append**:- Add/Append a value to key in redis. Syntax **Append [Key] [Value]**

```console
>Exist dataname
(integer)0
>Append dataname "first Data"
(integer)10
>Append dataname "; Second Data"
(integer)23
```

- **GET**:- Get the value of a key.

```console
> Get dataname
first Data; Second Data
```

- **SET**:- Set value of a key. Syntax **SET [Key] [Value]**

```console
>SET mykey 5
```

- **DECR**:- Decrement the value of a key by 1. Syntax **DECR [Key]**

```console
> DECR mykey
(integer) 4
>Get mykey
"4"
```

- **INCR**:- Increment the value of a key by 1.

```console
> INCR mykey
(integer) 5
```

- **DECRBY**:- Decrement the value of a key by value given. Syntax **DECRBY [Key] [decrement value]**

```console

>Get mykey
"5"

> DECRBY mykey 3
(integer) 3

```

- **INCRBY**:- Increment the value of a key by value given. Syntax **INCRBY [Key] [increment value]**

```console

>Get mykey
"3"

> INCRBY mykey 3
(integer) 6

```

- **STRLEN**:- Return the length of the string which is stored in key. Syntax **STRLEN [Key]**

## Redis Datatypes

- **Strings**:- Traditional String datatype.

- **Lists**:- Simply lists of string, sorted by insertion order. List command starts with letter **L**,**R**,**B**.
    1. LPUSH/LPOP
    2. LLEN/LINDEX
    3. RPUSH/RPOP
    4. LTRIM/LRANGE

```console

>LPUSH dbname "sqllite"
(integer) 1

>LPUSH dbname "mongodb"
(integer) 2

>LPUSH dbname "redis"
(integer) 3

>LRANGE dbname 0 3
1) "redis"
2) "mongodb"
3) "sqllite"

```

- **HASH**:- Redis hashes are map between string fields and string values. Perfext datatype to represent object. Redis hashes can store upto 4 billion item per hash. Redis functions generally starts with **H**.

    1. HSET/HGET/HGETALL

    2. HINCRBY

    3. HEXISTS

    4. HKEYS/HVALS

```console

>HMSET comment:101 text "Amazing Me" vote 10
OK

>HINCRBY comment:101 vote 15
(integer) 25

>HGETALL comment:101
1)"text"
2)"Amazing Me"
3)"vote"
4)"25"
```

- **SET**:-Contains distinct values. Unordered collection of strings. Set relevent commands starts with **S**.

    1. SADD/SREM/SCAN/SMOVE

    2. SPOP

    3. SDIFF/SDIFFSTORE

    4. SISMEMBER/SMEMBER

    5. SUNION/SINTER/SINTERSTORE

```console

>SADD name "John"
(integer) 1

>SADD name "Yash"
(interger) 2

>SADD name "Ahlawat"
(integer)

>SREM name "Ahlawat"
>SMEMBER name
1) John
2) Yash
```

- **SORTED SET**:- Contains unique items with Score value. Sorted Set related commands starts with **Z**. Redis sorted set can store 4 billions of values per set.

    1. ZADD/ZREM/ZSCAN

    2. ZRANK

    3. ZSCORE/ZRANGE

    4. ZCARD

```console

>ZADD myset 1 "john"
(integer) 0

>ZADD myset 2 "Yash"
(integer) 1

>ZADD myset 3 "Ahlawat"
(integer) 1

>ZRANGE myset 0 -1 withscore
1) "john"
2) "1"
3) "Yash"
4) "2"
5) "Ahlawat"
6) "3"
```

Feel free to contribute to it. To know more about me <a  href='https://yashpalahlawat.github.io/vitae/'>Click Here</a>.
