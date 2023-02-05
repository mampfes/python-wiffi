Release History
===============


1.1.1 (4-Feb-2023)
------------------

**Bugfix**

Add support for LAN based Wiffi devices: They don't send the attributes
`rssi` and `ssid`, but the old code always tried to get them. This resulted in the crash:

```
Traceback (most recent call last):
File "/usr/local/lib/python3.10/site-packages/wiffi/init.py", line 224, in call
await self.parse_msg(peername, data[:-1]) # omit separator with [:-1]
File "/usr/local/lib/python3.10/site-packages/wiffi/init.py", line 240, in parse_msg
metrics.append(WiffiMetricFromSystemInfo("rssi", "dBm", "number", data["Systeminfo"]["WLAN_Signal_dBm"]))
KeyError: 'WLAN_Signal_dBm'
```

This fix makes the attributes optional.

1.1.0 (25-Nov-2021)
-------------------

**Improvements**

Various usability enhancements esp. for Home Assistant:

- provide configuration url
- provide rssi as metric
- provide uptime as metric
- provide ssid as metric

1.0.0 (18-Apr-202)
-------------------

Initial revision.