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

### how to verify

``` bash
dig @127.0.0.1 -p 10053  www.google.com
dig @127.0.0.1 -p 10053  project-staging.foo.bar.
dig @127.0.0.1 -p 20053  www.google.com
dig @127.0.0.1 -p 20053  test.foo.bar
```