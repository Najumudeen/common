
### SD tips and tricks

### Latency and Throughput Performance in your system

### Availability

### PROXIES

1. Forward Proxy( generally referred as proxy)
```
Request :=  Client  ===> (Forward Proxy) ==> Server
Response := Server  ===> (Forward Proxy) ==> Client
```

IP Hiding by Forward Proxy
VPN works similar way

2. Reverse Proxy

Reverse Proxies act on behalf of a server in an interaction between a client and server

> [!TIP]
> Popular example for Reverse Proxies is Nginx

```
Request :=  Client  ===> (Reverse Proxy) ==> Server
```

it'a act behind of server

it can filter out requests that you want to ignore

### Logging

Metrics ( About Traffic, User .. etc)

Cache Stuff ( Putting data in memory)

### Load Balancing

### CACHING
```
Caching temporary storage
Data stored in RAM
Reduce or improve the latency of a system
```

##### Browser Cache (client Level)

when a user visits a new website, their browser needs to download data to load and display the content on the page.<br/>
To speed up this process the next time a user visits the site, browsers cache the content on the page and save a copy of it.<br/>

##### Server level

client interacts with the server 20 times to get a piece of data, but maybe the server doesn't always need to go the database to retrieve data<br/>
Maybe Server only needs to go to the database once and we can have some form of cahae here at the server level (in memory)<br/>
You could also have a cache in-between two componets in a system. So maybe you could have a cache in-between a server and a database.<br/>

> [!TIP]
> Redis is one of the most popular Caching

if data changing regulariy then we have to fine tune and make it better

#### Caching Strategies:

if Data is constentely changing

Problem: Two source of truth

```
1. Write Through Cache

    Wrting data both in cache and db at the same time during data.
    You are going to hit cache and data base writing data
    User do network call to the server

2. Write Back Cache

    Only update data in cache.
    Cache and DB will out of sync.
    Updating the DB asynchronously values after that are stores in the cache.
    Every five minutes, every five hours.
    Make sure that cache data is important
    Care of HA of data
```

#### Stale Cache

Out dated your data in cache
Write/Edit Comment on the server
The server data will not updated other servers.


### Get ride of state data
```
User => Server => Redis
Redis => Server => User1
Redis => Server => User2
```