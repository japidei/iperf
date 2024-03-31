# iperf3

## Docker install

docker-compose.yml

```
version: '3'

services:
  test:
    build:
      context: iperf3
      dockerfile: Dockerfile
    container_name: "iperf3"
    ports:
      - "50001:5001/tcp"
      - "50001:5001/udp"
    networks:
      - public
      - private
    dns_search: .
    command: iperf3 -s -V -d -p 5001

networks:
  public:
    driver: bridge
  private:
    driver: bridge
```

## Tests

### imac

```sh
$ iperf3 -c imac.local -p 50001
Connecting to host imac.local, port 50001
[  7] local ***** port 60154 connected to ***** port 50001
[ ID] Interval           Transfer     Bitrate
[  7]   0.00-1.00   sec   113 MBytes   947 Mbits/sec
[  7]   1.00-2.00   sec   110 MBytes   925 Mbits/sec
[  7]   2.00-3.00   sec   110 MBytes   924 Mbits/sec
[  7]   3.00-4.00   sec   111 MBytes   927 Mbits/sec
[  7]   4.00-5.00   sec   110 MBytes   926 Mbits/sec
[  7]   5.00-6.00   sec   110 MBytes   925 Mbits/sec
[  7]   6.00-7.00   sec   110 MBytes   926 Mbits/sec
[  7]   7.00-8.00   sec   110 MBytes   925 Mbits/sec
[  7]   8.00-9.00   sec   110 MBytes   926 Mbits/sec
[  7]   9.00-10.00  sec   109 MBytes   913 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate
[  7]   0.00-10.00  sec  1.08 GBytes   926 Mbits/sec                  sender
[  7]   0.00-10.04  sec  1.08 GBytes   922 Mbits/sec                  receiver
```

### rpi4

```
$ iperf3 -c 192.168.1.5 -p 50001
Connecting to host 192.168.1.5, port 50001
[  5] local 192.168.1.10 port 49750 connected to 192.168.1.5 port 50001
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   112 MBytes   938 Mbits/sec    0    387 KBytes
[  5]   1.00-2.00   sec   112 MBytes   940 Mbits/sec    0    445 KBytes
[  5]   2.00-3.00   sec   112 MBytes   939 Mbits/sec    0    467 KBytes
[  5]   3.00-4.00   sec   111 MBytes   931 Mbits/sec    0    467 KBytes
[  5]   4.00-5.00   sec   113 MBytes   946 Mbits/sec    0    467 KBytes
[  5]   5.00-6.00   sec   111 MBytes   931 Mbits/sec    0    467 KBytes
[  5]   6.00-7.00   sec   112 MBytes   938 Mbits/sec    0    467 KBytes
[  5]   7.00-8.00   sec   113 MBytes   945 Mbits/sec    0    467 KBytes
[  5]   8.00-9.00   sec   112 MBytes   937 Mbits/sec    0    467 KBytes
[  5]   9.00-10.00  sec   112 MBytes   938 Mbits/sec    0    624 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.09 GBytes   938 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.09 GBytes   932 Mbits/sec                  receiver

iperf Done.
```

