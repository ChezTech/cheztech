
[//]: # (Note: I need to wrap all bare links with angle brackets, <...> in order for GitHub to convert the .md into .html for static web pages.)



test line breaks
second line, nothing special

test again\
second line, backslash trailing

and again \
second line, space and backslash

two spaces  
after that line (which get removed since I have remove trailing whitespace set - now I can save that)

using a html break<\br>
will make a second line, but is the ugliest of all

used the wrong slash<br/>
in the html break


now about links

www.example.com

http://www.example.com

https://www.example.com

https://github.com/esnet/iperf

*https://github.com/esnet/iperf
* https://github.com/esnet/iperf


Use NAS (Synology 918+) to test local network performance.

use _iPerf3_
* <https://software.es.net/iperf/>
* <https://github.com/esnet/iperf>

I found this topic: <https://forum.synology.com/enu/viewtopic.php?f=27&t=115257>\
A user by the name of _jadahl_ compiled _iPerf3_ for Synology DSM\
His website is here: <http://www.jadahl.com>, binaries can be found here: <http://www.jadahl.com/iperf/>

I grabbed this version: <http://www.jadahl.com/iperf/DSM_6.1/iperf_apollolake-6.1_3.2-1.spk>

Install in Synology using Package Center - Manual Install

Make sure `ssh` is enabled in Control Panel->Terminal & SNMP section


Grab a _iPerf3_ build for your client
* <https://software.es.net/iperf/obtaining.html>

Running: <https://software.es.net/iperf/invoking.html>

Windows client - using Wi-Fi

against a public iPerf server:
* List here: <https://iperf.fr/iperf-servers.php>
* This one seems nice: <https://iperf.scottlinux.com/>


```
C:>iperf3 -c iperf.scottlinux.com
Connecting to host iperf.scottlinux.com, port 5201
[  4] local 10.0.0.139 port 60348 connected to 45.33.39.39 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.01   sec  1.38 MBytes  11.4 Mbits/sec
[  4]   1.01-2.00   sec  1.38 MBytes  11.6 Mbits/sec
[  4]   2.00-3.01   sec  1.50 MBytes  12.5 Mbits/sec
[  4]   3.01-4.00   sec  1.38 MBytes  11.6 Mbits/sec
[  4]   4.00-5.00   sec  1.38 MBytes  11.5 Mbits/sec
[  4]   5.00-6.00   sec  1.38 MBytes  11.6 Mbits/sec
[  4]   6.00-7.00   sec  1.50 MBytes  12.6 Mbits/sec
[  4]   7.00-8.01   sec  1.38 MBytes  11.5 Mbits/sec
[  4]   8.01-9.00   sec  1.38 MBytes  11.6 Mbits/sec
[  4]   9.00-10.00  sec  1.38 MBytes  11.5 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-10.00  sec  14.0 MBytes  11.7 Mbits/sec                  sender
[  4]   0.00-10.00  sec  13.9 MBytes  11.7 Mbits/sec                  receiver

iperf Done.
```


Now, let's test locally.
* <https://fasterdata.es.net/performance-testing/network-troubleshooting-tools/iperf/>


`ssh` into your NAS

```
$ iperf3 -s
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
```

```
C:>iperf3 -c 10.0.0.5
Connecting to host 10.0.0.5, port 5201
[  4] local 10.0.0.139 port 60386 connected to 10.0.0.5 port 5201
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.01   sec  4.50 MBytes  37.5 Mbits/sec
[  4]   1.01-2.00   sec  4.75 MBytes  40.1 Mbits/sec
[  4]   2.00-3.01   sec  5.00 MBytes  41.8 Mbits/sec
[  4]   3.01-4.00   sec  5.88 MBytes  49.5 Mbits/sec
[  4]   4.00-5.00   sec  5.88 MBytes  49.3 Mbits/sec
[  4]   5.00-6.00   sec  6.00 MBytes  50.3 Mbits/sec
[  4]   6.00-7.00   sec  5.25 MBytes  44.0 Mbits/sec
[  4]   7.00-8.00   sec  5.88 MBytes  49.3 Mbits/sec
[  4]   8.00-9.00   sec  5.62 MBytes  47.2 Mbits/sec
[  4]   9.00-10.00  sec  5.50 MBytes  46.2 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-10.00  sec  54.2 MBytes  45.5 Mbits/sec                  sender
[  4]   0.00-10.00  sec  54.2 MBytes  45.5 Mbits/sec                  receiver

iperf Done.
```

on the server side you'll see:

```
Accepted connection from 10.0.0.139, port 60385
[  5] local 10.0.0.5 port 5201 connected to 10.0.0.139 port 60386
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-1.00   sec  4.33 MBytes  36.4 Mbits/sec
[  5]   1.00-2.00   sec  4.82 MBytes  40.5 Mbits/sec
[  5]   2.00-3.00   sec  4.99 MBytes  41.9 Mbits/sec
[  5]   3.00-4.00   sec  5.87 MBytes  49.2 Mbits/sec
[  5]   4.00-5.00   sec  5.81 MBytes  48.7 Mbits/sec
[  5]   5.00-6.00   sec  6.04 MBytes  50.7 Mbits/sec
[  5]   6.00-7.00   sec  5.23 MBytes  43.9 Mbits/sec
[  5]   7.00-8.00   sec  5.89 MBytes  49.4 Mbits/sec
[  5]   8.00-9.00   sec  5.62 MBytes  47.2 Mbits/sec
[  5]   9.00-10.00  sec  5.55 MBytes  46.6 Mbits/sec
[  5]  10.00-10.02  sec  90.9 KBytes  49.6 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.02  sec  54.2 MBytes  45.4 Mbits/sec                  receiver
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
```
