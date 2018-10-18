```
[libdefaults]
default_realm = HADOOP.COM
dns_lookup_kdc = false
dns_lookup_realm = false
ticket_lifetime = 86400
renew_lifetime = 604800
forwardable = true
default_tgs_enctypes = aes128-cts
default_tkt_enctypes = aes128-cts
permitted_enctypes = aes128-cts
udp_preference_limit = 1
kdc_timeout = 3000
[realms]
HADOOP.COM = {
kdc = gianbo01.northeurope.cloudapp.azure.com
admin_server = gianbo01.northeurope.cloudapp.azure.com
}
[domain_realm]
```
