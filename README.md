## Installing dependencies

```
apt-get install -y docker.io
apt-get install -y ruby bundler
```

## Installing ETCD

Install etcd on a docker image

```
docker.io run --name etcd -d -p 4001:4001 -p 7001:7001 coreos/etcd
```

## Installing HAProxy
Use the apt-get command to install HAProxy.

```
apt-get install haproxy
```

We need to enable HAProxy to be started by the init script.

```
nano /etc/default/haproxy
```

Set the ENABLED option to 1

```
ENABLED=1
```

To check if this change is done properly execute the init script of HAProxy without any parameters. You should see the following.

```
root@haproxy:~# service haproxy
Usage: /etc/init.d/haproxy {start|stop|reload|restart|status}
```

As root :

```
echo "haproxy ALL=(ALL) NOPASSWD: /usr/sbin/service haproxy reload$" > /etc/sudoers.d/haproxy
chgrp haproxy /etc/haproxy/haproxy.cfg
chmod g+rw /etc/haproxy/haproxy.cfg
```

## Install smartstack

As user:

```

bundle
bundle exec nerve --config nerve.conf
bundle exec synapse --config synapse.conf
```
