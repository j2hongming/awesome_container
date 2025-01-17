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