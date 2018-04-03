# redis-sentinel
A container that runs a sentinal instance

## Example
```bash
docker-compose up
```

this will run five containers:
```
docker ps

fa7cd7aceef5        redissentinel_sentinel-one   "sentinel-entrypoi..."   About a minute ago   Up About a minute   6379/tcp, 26379/tcp   redissentinel_sentinel-one_1
4afb45e2784c        redissentinel_sentinel-two   "sentinel-entrypoi..."   About a minute ago   Up About a minute   6379/tcp, 26379/tcp   redissentinel_sentinel-two_1
624c507adeea        redis:4.0.9-alpine           "docker-entrypoint..."   14 minutes ago       Up About a minute   6379/tcp              redissentinel_redis-slave-two_1
8e9328678dd0        redis:4.0.9-alpine           "docker-entrypoint..."   14 minutes ago       Up About a minute   6379/tcp              redissentinel_redis-slave-one_1
de220d008b95        redis:4.0.9-alpine           "docker-entrypoint..."   14 minutes ago       Up About a minute   6379/tcp              redissentinel_redis-master_1
```

- master: The master redis containers
- slaves: slaves of the master
- sentinel: the two instances of sentinel running


Environment:
```
SENTINEL_QUORUM 1

SENTINEL_DOWN_AFTER 1000

SENTINEL_FAILOVER 1000

REDIS_MASTER redis-master
```
> These are defaults that can be changed by setting the coreesponding environment variables

# Test Fail Over
if you kill the master container you should be able to see one of the slaves get selected as the master instance by sentinel
