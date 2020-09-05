

1. Site Survey with LInux
Signal strength (One shot/sorted by strength
 ```
nmcli d wifi
```

sorted by ssid

```
nmcli -f "CHAN,BARS,SIGNAL,SSID" d wifi list ifname wlx10feed21ae1d  | sort -n
```

continuous

```
watch  "nmcli -f "CHAN,BARS,SIGNAL,SSID" d wifi list ifname wlx10feed21ae1d  | sort -n"
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUwNjE4MDEwNl19
-->