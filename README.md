Socket.io benchmarking tool
=============

A benchmark tool aimed at stress testing scale nodes which consist by node.js + socket.io(1.0.2) + socket.io-redis

## Usage
```script
Usage:
    -n     <number>   total request number to be sent
    -c     <number>   concurrency number, the same workers number
    --ioc  <number>   clients number in per worker
    -t     <number>   interval time for emitting in per worker(ms)
    [ws://]hostname[:port]/path

e.g:
   DEBUG=benchmark:* ./bin/nb -n 1000 -c 10 --ioc 10 -t 20000 ws://localhost:3000
```

## Result
```script
* PC info
- IP   : 192.168.20.203
- Port : 9401
- model name	: QEMU Virtual CPU version (cpu64-rhel6)
- cpu MHz       : 2199.998
- Mem           : 1877MB

|------+-----+------+---------+-------+-----+--------+----------+------|
| conc | ioc | intv |  ReqNum |   Max | Min |    avg |     cpu% | mem% |
|------+-----+------+---------+-------+-----+--------+----------+------|
|   10 |  10 | 2000 |   52300 |   626 |   2 |     47 |      4.0 |  4.1 |
|   10 |  20 | 2000 |  189627 |   899 |   2 |     72 |        8 |  9.1 |
|------+-----+------+---------+-------+-----+--------+----------+------|
|   10 |  30 | 2000 |  806416 |  5615 |  11 |   2462 |       11 |  4.4 |
|   10 |  30 | 3000 |  689939 |  1252 |   2 |    105 |        9 |  4.4 |
|   10 |  30 | 4000 |  442500 |   637 |   2 |     38 |        6 |  4.3 |
|------+-----+------+---------+-------+-----+--------+----------+------|
|   10 |  40 | 3000 | 1154760 | 68664 |   7 | 19000+ | unstable |   20 |
|   10 |  40 | 4000 | 1529954 |  6261 |  13 |  2845+ |        8 |  4.7 |
|   10 |  40 | 5000 |  817200 |  1515 |   2 |     70 |        8 |  7.7 |
|------+-----+------+---------+-------+-----+--------+----------+------|
|   10 |  50 | 5000 | 2234162 | 11351 |  12 |   4607 |   8 ~ 15 |  7.8 |
|   10 |  50 | 6000 |    2542 |  7386 |   8 |   2664 |        7 |  4.9 |
|   10 |  50 | 7000 | 1218472 |   684 |   2 |     77 |        6 |  5.6 |


```

## More

If you have not socket.io server with latest version,
U can checkout `https://github.com/luckyan315/chat.git`,
It's a simple chatting room impl with sio(1.0.2)
