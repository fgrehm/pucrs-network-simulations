# pucrs-network-simulations

Experimenting with networking conditions

## Start the VMs

```sh
vagrant up --provider=virtualbox
```

## TCP tests

Start the server:

```sh
vagrant ssh server -c 'iperf -s'
```

Log in into the client box:

```sh
vagrant ssh client
```

Capture data:

```sh
cd /vagrant
scripts/tcp-tests /vagrant/output/01-baseline-tcp && \

scripts/toggle-variable-latency on \
&& scripts/tcp-tests /vagrant/output/02-var-latency-tcp \
&& scripts/toggle-variable-latency off && \

scripts/toggle-packet-loss on \
&& scripts/tcp-tests /vagrant/output/03-packet-loss-tcp \
&& scripts/toggle-packet-loss off
```

## UDP tests

Start the server:

```sh
vagrant ssh server -c 'iperf -s -u'
```

Log in into the client box:

```sh
vagrant ssh client
```

Capture data:

```sh
cd /vagrant
scripts/udp-tests /vagrant/output/01-baseline-udp && \

scripts/toggle-variable-latency on \
&& scripts/udp-tests /vagrant/output/02-var-latency-udp \
&& scripts/toggle-variable-latency off && \

scripts/toggle-packet-loss on \
&& scripts/udp-tests /vagrant/output/03-packet-loss-udp \
&& scripts/toggle-packet-loss off
```
