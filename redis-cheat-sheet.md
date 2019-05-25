# Redis Cheat Sheet

Start Redis
```
/opt/redis-5.0.5/src$ ./redis-server
```

Check if Redis is working
```
/opt/redis-5.0.5/src$ ./redis-cli ping
PONG
```

```
/opt/redis-5.0.5/src$ ./redis-cli
127.0.0.1:6379>ping
PONG
127.0.0.1:6379>set mykey somevalue
OK
127.0.0.1:6379>get mykey
"somevalue"
```
