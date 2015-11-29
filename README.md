# pucrs-network-simulations

Experimenting with networking conditions

## Start the VMs

```sh
vagrant up --no-parallel
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
scripts/run-all-tcp-tests
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
scripts/run-all-udp-tests
```


