# pucrs-network-simulations

Experimenting with networking conditions

## Server

```sh
vagrant ssh server -c 'iperf -s'
```

## Client

```sh
vagrant ssh client

# Baseline
iperf -c 192.168.33.10 -i 1 -w 1K

# 100ms delay for network interface
sudo tc qdisc add dev eth1 root netem delay 100ms
iperf -c 192.168.33.10 -i 1 -w 1K
sudo tc qdisc del dev eth1 root netem delay 100ms
```
