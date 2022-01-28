```python

  _____  _   _  _____   _____                        _       _____                                  
 |  __ \| \ | |/ ____| |  __ \                      | |     |  __ \                                 
 | |  | |  \| | (___   | |__) |___  ___ ___  _ __ __| |___  | |  | |_   _ _ __ ___  _ __   ___ _ __ 
 | |  | | . ` |\___ \  |  _  // _ \/ __/ _ \| '__/ _` / __| | |  | | | | | '_ ` _ \| '_ \ / _ \ '__|
 | |__| | |\  |____) | | | \ \  __/ (_| (_) | | | (_| \__ \ | |__| | |_| | | | | | | |_) |  __/ |   
 |_____/|_| \_|_____/  |_|  \_\___|\___\___/|_|  \__,_|___/ |_____/ \__,_|_| |_| |_| .__/ \___|_|   
                                                                                   | |              
                                                                                   |_|              
```
A dns records dump tool | DNS记录转储工具
Reference：https://github.com/dirkjanm/adidnsdump


## how to use?
```python

Required options:
  HOSTNAME              Hostname/ip or ldap://host:port connection string to
                        connect to

Main options:
  -h, --help            show this help message and exit
  -u USERNAME, --user USERNAME
                        DOMAIN\username for authentication.
  -p PASSWORD, --password PASSWORD
                        Password or LM:NTLM hash, will prompt if not specified
  --forest              Search the ForestDnsZones instead of DomainDnsZones
  --legacy              Search the System partition (legacy DNS storage)
  --zone ZONE           Zone to search in (if different than the current
                        domain)
  --print-zones         Only query all zones on the DNS server, no other
                        modifications are made
  -v, --verbose         Show verbose info
  -d, --debug           Show debug info
  -r, --resolve         Resolve hidden recoreds via DNS
  --dns-tcp             Use DNS over TCP
  --include-tombstoned  Include tombstoned (deleted) records
  --ssl                 Connect to LDAP server using SSL
  --referralhosts       Allow passthrough authentication to all referral hosts
  --dcfilter            Use an alternate filter to identify DNS record types
  --sslprotocol SSLPROTOCOL
                        SSL version for LDAP connection, can be SSLv23, TLSv1,
                        TLSv1_1 or TLSv1_2
```

example:
```bash
$ DNSRecordsDumper.exe -u 1bit\administrator -p 123456 192.168.66.66

Connecting to host...
Binding to host
Bind OK
Querying zone for records
{'type': 'A', 'name': u'ForestDnsZones', 'value': '192.168.66.66'}
{'type': 'A', 'name': u'ForestDnsZones', 'value': '192.168.88.68'}
{'type': 'A', 'name': u'exchange', 'value': '192.168.66.16'}
{'type': 'A', 'name': u'DomainDnsZones', 'value': '192.168.66.66'}
{'type': 'A', 'name': u'DomainDnsZones', 'value': '192.168.88.68'}
{'type': 'A', 'name': u'dc2', 'value': '192.168.66.66'}
{'type': 'A', 'name': u'dc2', 'value': '192.168.88.68'}
{'type': 'NS', 'name': u'_msdcs', 'value': u'dc2.1bit.lab.'}
{'type': 'A', 'name': u'@', 'value': '192.168.88.68'}
{'type': 'A', 'name': u'@', 'value': '192.168.66.66'}
{'type': 'NS', 'name': u'@', 'value': u'dc2.1bit.lab.'}
Found 11 records,check File: DnsRecords.csv
```
