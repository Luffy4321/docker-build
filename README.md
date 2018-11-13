# docker-build

[![GitHub commit activity the past week, 4 weeks, year](https://img.shields.io/github/commit-activity/y/eslint/eslint.svg)](https://github.com/kometchtech/docker-build/commits/master)
[![GitHub last commit](https://img.shields.io/github/last-commit/google/skia.svg)](https://github.com/kometchtech/docker-build/commits/master)
[![GitHub repo size in bytes](https://img.shields.io/github/repo-size/badges/shields.svg)](https://github.com/kometchtech/docker-build)

personal docker build

It exists to check the operation of container in the ARM environment (arm64/Aarch64).
> For arm32, tackle depending on the mood.

Basically we will check the operation of the following application.

## base images

- Debian stretch/testing
- [arm64v8/alpine](https://hub.docker.com/r/arm64v8/alpine/)

## check software

- dibbler-server <http://klub.com.pl/dhcpv6/>
- NSD <https://www.nlnetlabs.nl/projects/nsd/>
- Unbound <https://www.nlnetlabs.nl/projects/unbound/>
- PowerDNS recursor <https://www.powerdns.com/recursor.html>
- Knot DNS resolver <https://www.knot-resolver.cz/>
- Knot DNS <https://www.knot-dns.cz/>  
~~- CoreDNS (testing) <https://coredns.io/>~~  
Currently the Docker image is released from CoreDNS.io formula. <https://hub.docker.com/r/coredns/coredns/>
- dnsdist <https://dnsdist.org/>
- BIND9 (testing) <https://www.isc.org/downloads/bind/> alpine package
- zabbix-agent (testing) <https://www.zabbix.com/>
- mackerel-agent-plugins (testing) <https://github.com/mackerelio/mackerel-agent-plugins>
- DNSCrypt Proxy <https://github.com/jedisct1/dnscrypt-proxy>
- Stubby <https://github.com/getdnsapi/stubby>

## Tips

- configuration IPv6

```bash
echo '{"ipv6":true, "fixed-cidr-v6":"2001:db8:1::/64"}' | sudo tee -a /etc/docker/daemon.json
sudo systemctl restart docker.service
```
- If you make the Interface
```
docker network create --ipv6 \
    --gateway 2001:db8:1::1 \
    --subnet 2001:db8:1::/80 \
    docker-ipv6-network
```

