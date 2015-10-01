# watchif
A script to watch a network interface for drops and trigger mtr against a destination if they happen. 

This assumes you have mtr installed

Usage: watchif [interface: re eth0] [destination to trace to: re wwww.google.com]

RE: watchif eth0 www.google.com

Will produce something like:

<pre>
host:~# ./watchif eth0 www.google.com
DEBUG - base_tx_dropped: 0
DEBUG - base_rx_dropped: 6921
DEBUG - base_rx_dropped now changed to 6922
Start: Thu Oct  1 06:14:45 2015
HOST: chef.oak.vast.com                   Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- vlan8-coreswitch2.oak.vast.com       0.0%    10    0.3   0.4   0.3   0.5   0.0
  2.|-- fw-bg-3-0.oak.vast.com               0.0%    10    0.7   0.6   0.3   1.2   0.0
  3.|-- ge-0-0-0.border2.oak.vast.com       30.0%    10    1.7   1.1   0.7   1.7   0.0
  4.|-- 208.185.33.1                         0.0%    10    2.6   1.6   1.0   3.2   0.7
  5.|-- xe-0-3-0.mpr1.sjc37.us.zip.zayo.com  0.0%    10    1.9   8.4   1.4  57.1  17.2
  6.|-- xe-5-2-0.cr2.sjc2.us.zip.zayo.com    0.0%    10   10.2   6.2   2.1  28.2   8.1
  7.|-- ae10.mpr4.sjc7.us.zip.zayo.com       0.0%    10    3.1   5.0   2.4  11.6   2.8
  8.|-- 74.125.49.13                         0.0%    10    4.5   4.3   2.7   7.5   1.5
  9.|-- 216.239.49.168                       0.0%    10   28.5   8.5   2.8  28.5   8.7
 10.|-- 209.85.246.20                        0.0%    10   30.4  14.9   4.5  42.2  14.4
 11.|-- 216.239.46.240                       0.0%    10   30.1  30.2  27.8  34.4   2.1
 12.|-- 216.239.51.108                       0.0%    10   50.6  51.3  49.9  55.3   1.5
 13.|-- 209.85.243.145                       0.0%    10  146.2 148.3 146.2 151.5   1.6
 14.|-- 216.239.46.216                       0.0%    10   68.2  69.4  67.0  73.9   2.2
 15.|-- 209.85.242.149                       0.0%    10  146.7 145.6 144.3 150.2   1.7
 16.|-- 72.14.235.16                        10.0%    10  147.1 147.0 145.9 149.0   0.8
 17.|-- 216.239.56.172                       0.0%    10  146.9 148.1 146.5 153.5   2.4
 18.|-- 66.249.94.143                       10.0%    10  146.1 147.2 146.1 148.0   0.4
 19.|-- fra07s64-in-f19.1e100.net           10.0%    10  147.3 147.1 146.2 148.4   0.5
</pre>

The simplest execution is just to run this under screen and output to a file. Alternately you could set it up under something like supervisord.
