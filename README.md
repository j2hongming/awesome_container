# awesome_container
Collect the awesome container

## [Nexus](https://hub.docker.com/r/sonatype/nexus3/)
### prerequisite
1. prepare the `keystore.jks` with `-storepass` and `-keypass`
```
keytool -genkeypair -keystore keystore.jks -storepass foo@bar -alias foo.com -keyalg RSA -keysize 2048 -validity 5000 -keypass foo@bar -dname 'CN=*.foo.com, OU=Sonatype, O=Sonatype, L=Unspecified, ST=Unspecified, C=US' -ext 'SAN=DNS:nexus.foo.com,DNS:bar.foo.com,DNS:repo.foo.com'
```
2. change the `KeyStorePassword`, `KeyManagerPassword` and `TrustStorePassword`

``` bash
docker compose up -d
```
access the **https://{Nexus FQDN}:28443**

## DNS

### bind

- [bind9 with webmin console](https://hub.docker.com/r/sameersbn/bind)
- [ubuntu/bind9](https://hub.docker.com/r/ubuntu/bind9)

#### prerequisite

For bind9 with webmin console
``` bash
mkdir -p dns_data_with_webadmin
```

For ubuntu/bind9
``` bash
mkdir -p dns_data/bind/etc
mkdir -p dns_data/bind/lib
cp bind9/named.conf.options dns_data/bind/etc/
cp bind9/foo.bar.hosts dns_data/bind/lib/
```

#### launch

For bind9 with webmin console
``` bash
docker compose up -d dns-bind9-webadmin
```

For ubuntu/bind9
``` bash
docker compose up -d dns-bind9
```

### coredns

``` bash
docker compose up -d dns-coredns
```