# PFSense Parser

This parser works for PFSense, tested with a PFSense instance running version 2.4.4

This only focuses on the filterlogs as described in the [documentation](https://docs.netgate.com/pfsense/en/latest/monitoring/filter-log-format-for-pfsense-2-2.html)

# Important

You have to change the timezone in the `parseTimestamp` line unless you are logging in UTC

# Tests
```
<134>Mar 18 12:44:33 filterlog: 9,,,1000000103,igb0,match,block,in,4,0x0,,244,13575,0,none,6,tcp,40,194.26.69.100,176.23.153.231,59560,6533,0,S,2692134245,,1024,,
```

```
<134>Mar  2 05:58:55 filterlog: 9,,,1000000103,igb0,match,block,in,4,0x0,,50,10073,0,none,1,icmp,34,45.87.167.22,87.104.81.209,request,10073,014
```

```
<134>Mar  3 02:00:06 filterlog: 71,,,1581371822,igb0,match,pass,in,4,0x0,,51,36828,0,none,6,tcp,44,78.62.199.18,87.104.81.209,52605,8080,0,S,1466454481,,6292,,mss
```

```
Mar  3 01:59:15 filterlog: 6,,,1000000004,igb3,match,block,out,6,0x00,0x00000,1,Options,0,36,fe80::1:1,ff02::16,HBH,PADN,RTALERT,0x0000,
```


## Resources:
* [PFSense filterlog format](https://docs.netgate.com/pfsense/en/latest/monitoring/filter-log-format-for-pfsense-2-2.html)