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
You may wonder that here I have aes128-cts instead of aes256-cts: the reason is that I had a lot of problems with aes256 because I had the JDK 1.7 instead of 1.8 (why I installed 1.7 ? I really don't know, probably I was drunk)
but the default of MIT KDC is aes256-cts that was used when I created the admin principal.
For this reason I forced to use aes128-cts and it worked, even if in a true installation I'll use always aes256 encryption.
