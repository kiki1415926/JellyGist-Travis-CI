# ifconfig

对应 Windows 中的`网络共享中心`：

![network-setting](ifconfig/network-setting.png)

显示当前活跃的网络连接信息，主要用来看设备的 ip 地址以及 MAC 地址。

```bash
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:90:5a:2a:02
          inet addr:128.100.31.200  Bcast:128.100.31.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe5a:2a02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834718767 errors:0 dropped:1631414 overruns:993 frame:0
          TX packets:983664109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:557689808295 (557.6 GB)  TX bytes:1152034651284 (1.1 TB)
          Memory:dff20000-dff3ffff

eth1      Link encap:Ethernet  HWaddr 00:25:90:5a:2a:03
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe5a:2a03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8568470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43499383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:580635402 (580.6 MB)  TX bytes:62390089478 (62.3 GB)
          Memory:dff60000-dff7ffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2820987923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2820987923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:233420505104 (233.4 GB)  TX bytes:233420505104 (233.4 GB)
```

## Alternative

这里不得不提一句 `ifconfig` 的接班人 `ip` 命令，它的功能更加强大，这里我仅仅演示一下如何查询本地 ip 地址。在上面我们看到当前服务器下有多条 link，我们通常只关心 `eth0`，因为单路网卡在家庭中最为常见。

```bash
$ ip addr show eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:25:90:5a:2a:02 brd ff:ff:ff:ff:ff:ff
    inet 128.100.31.200/24 brd 128.100.31.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::225:90ff:fe5a:2a02/64 scope link
       valid_lft forever preferred_lft forever
```