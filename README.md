# Synapse and nerve mini-howto

- Install haproxy from your distribution.
- Install zookeeper from your distribution or official site.


As root ( change $username and $groupname accordingly):

```bash
echo "$username ALL=(ALL) NOPASSWD: /usr/sbin/service haproxy reload" > /etc/sudoers.d/haproxy
chgrp $groupname /etc/haproxy/haproxy.cong
chmod g+rw /etc/haproxy/haproxy.cong
```

As user:

``bash
bundle
bundle exec nerve --config nerve.conf
bundle exec synapse --config synapse.conf
```