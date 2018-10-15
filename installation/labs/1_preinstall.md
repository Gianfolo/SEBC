1. Check vm.swappiness on all your nodes
```
[gianbo@gianbo01 ~]$ sudo bash -c "echo 'vm.swappiness = 1' >> /etc/sysctl.conf" && sudo sysctl vm.swappiness=1
vm.swappiness = 1
```

2. Show the mount attributes of your volume
```
[gianbo@gianbo01 ~]$ cat /proc/mounts
rootfs / rootfs rw 0 0
proc /proc proc rw,relatime 0 0
sysfs /sys sysfs rw,relatime 0 0
devtmpfs /dev devtmpfs rw,relatime,size=8215132k,nr_inodes=2053783,mode=755 0 0
devpts /dev/pts devpts rw,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /dev/shm tmpfs rw,relatime 0 0
/dev/sda2 / ext4 rw,relatime,barrier=1,data=ordered,discard 0 0
/proc/bus/usb /proc/bus/usb usbfs rw,relatime 0 0
/dev/sda1 /boot ext4 rw,relatime,barrier=1,data=ordered,discard 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
/dev/sdb1 /mnt/resource ext4 rw,noatime,barrier=1,data=ordered,discard 0 0
```

3. Show the reserve space of any non-root, ext-based volumes
```
[gianbo@gianbo01 ~]$ sudo tune2fs -l /dev/sdc1 | grep 'Reserved block count'
Reserved block count:     262140
```

4. Disable transparent hugepage support
```
[gianbo@gianbo01 ~]$ sudo bash -c "echo 'never' > /sys/kernel/mm/transparent_hugepage/defrag"
[gianbo@gianbo01 ~]$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

```

On the Cloudera CentOS 6.8 that we used the transarent hugepage support is already disabled.

5. List your network interface configuration
```
[gianbo@gianbo01 ~]$ /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:3A:B7:DF:AC
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5615554 (5.3 MiB)  TX bytes:2106483 (2.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

6. List forward and reverse host lookups using getent or nslookup
```
[gianbo@gianbo01 ~]$ nslookup gianbo02
Server:         168.63.129.16
Address:        168.63.129.16#53

Name:   gianbo02.ho1bvs2ww1ju5nzojvplbjp0vf.fx.internal.cloudapp.net
Address: 10.0.0.5

[gianbo@gianbo01 ~]$ nslookup gianbo03
Server:         168.63.129.16
Address:        168.63.129.16#53

Name:   gianbo03.ho1bvs2ww1ju5nzojvplbjp0vf.fx.internal.cloudapp.net
Address: 10.0.0.6

[gianbo@gianbo01 ~]$ nslookup gianbo04
Server:         168.63.129.16
Address:        168.63.129.16#53

Name:   gianbo04.ho1bvs2ww1ju5nzojvplbjp0vf.fx.internal.cloudapp.net
Address: 10.0.0.7

[gianbo@gianbo01 ~]$ nslookup gianbo05
Server:         168.63.129.16
Address:        168.63.129.16#53

Name:   gianbo05.ho1bvs2ww1ju5nzojvplbjp0vf.fx.internal.cloudapp.net
Address: 10.0.0.8
```

Check using getent:
```
[gianbo@gianbo01 ~]$ getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
10.0.0.4        gianbo01
10.0.0.5        gianbo02
10.0.0.6        gianbo03
10.0.0.7        gianbo04
10.0.0.8        gianbo05
```

7. Show the nscd service is running
```
[gianbo@gianbo01 ~]$ ps -edaf |grep nscd
gianbo     1830   1736  0 08:43 pts/0    00:00:00 grep nscd
```

Install the service:
```
[gianbo@gianbo01 ~]$ sudo yum install nscd
Loaded plugins: fastestmirror
Setting up Install Process
Determining fastest mirrors
base                                                                                                                                             | 3.7 kB     00:00
base/primary_db                                                                                                                                  | 4.7 MB     00:00
extras                                                                                                                                           | 3.4 kB     00:00
extras/primary_db                                                                                                                                |  26 kB     00:00
openlogic                                                                                                                                        | 2.9 kB     00:00
openlogic/primary_db                                                                                                                             | 541 kB     00:00
updates                                                                                                                                          | 3.4 kB     00:00
updates/primary_db                                                                                                                               | 1.9 MB     00:00
Resolving Dependencies
--> Running transaction check
---> Package nscd.x86_64 0:2.12-1.212.el6 will be installed
--> Processing Dependency: glibc = 2.12-1.212.el6 for package: nscd-2.12-1.212.el6.x86_64
--> Running transaction check
---> Package glibc.x86_64 0:2.12-1.209.el6_9.2 will be updated
--> Processing Dependency: glibc = 2.12-1.209.el6_9.2 for package: glibc-common-2.12-1.209.el6_9.2.x86_64
---> Package glibc.x86_64 0:2.12-1.212.el6 will be an update
--> Running transaction check
---> Package glibc-common.x86_64 0:2.12-1.209.el6_9.2 will be updated
---> Package glibc-common.x86_64 0:2.12-1.212.el6 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================================================
 Package                                    Arch                                 Version                                       Repository                          Size
========================================================================================================================================================================
Installing:
 nscd                                       x86_64                               2.12-1.212.el6                                base                               232 k
Updating for dependencies:
 glibc                                      x86_64                               2.12-1.212.el6                                base                               3.8 M
 glibc-common                               x86_64                               2.12-1.212.el6                                base                                14 M

Transaction Summary
========================================================================================================================================================================
Install       1 Package(s)
Upgrade       2 Package(s)

Total download size: 18 M
Is this ok [y/N]: y
Downloading Packages:
(1/3): glibc-2.12-1.212.el6.x86_64.rpm                                                                                                           | 3.8 MB     00:00
(2/3): glibc-common-2.12-1.212.el6.x86_64.rpm                                                                                                    |  14 MB     00:01
(3/3): nscd-2.12-1.212.el6.x86_64.rpm                                                                                                            | 232 kB     00:00
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                    10 MB/s |  18 MB     00:01
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
Warning: RPMDB altered outside of yum.
  Updating   : glibc-2.12-1.212.el6.x86_64                                                                                                                          1/5
  Updating   : glibc-common-2.12-1.212.el6.x86_64                                                                                                                   2/5
  Installing : nscd-2.12-1.212.el6.x86_64                                                                                                                           3/5
  Cleanup    : glibc-2.12-1.209.el6_9.2.x86_64                                                                                                                      4/5
  Cleanup    : glibc-common-2.12-1.209.el6_9.2.x86_64                                                                                                               5/5
  Verifying  : glibc-common-2.12-1.212.el6.x86_64                                                                                                                   1/5
  Verifying  : nscd-2.12-1.212.el6.x86_64                                                                                                                           2/5
  Verifying  : glibc-2.12-1.212.el6.x86_64                                                                                                                          3/5
  Verifying  : glibc-2.12-1.209.el6_9.2.x86_64                                                                                                                      4/5
  Verifying  : glibc-common-2.12-1.209.el6_9.2.x86_64                                                                                                               5/5

Installed:
  nscd.x86_64 0:2.12-1.212.el6

Dependency Updated:
  glibc.x86_64 0:2.12-1.212.el6                                                   glibc-common.x86_64 0:2.12-1.212.el6

Complete!
```

```
[gianbo@gianbo01 ~]$ sudo service nscd start
Starting nscd:                                             [  OK  ]

[gianbo@gianbo01 ~]$ sudo chkconfig nscd on

[gianbo@gianbo01 ~]$ sudo chkconfig --list nscd
nscd            0:off   1:off   2:on    3:on    4:on    5:on    6:off
```


8. Show the ntpd service is running
```
[gianbo@gianbo01 ~]$ sudo chkconfig --list ntpd
error reading information on service ntpd: No such file or directory

[gianbo@gianbo01 ~]$ sudo yum install ntp ntpdate ntp-doc
Loaded plugins: fastestmirror
Setting up Install Process
Loading mirror speeds from cached hostfile
Resolving Dependencies
--> Running transaction check
---> Package ntp.x86_64 0:4.2.6p5-12.el6.centos.2 will be installed
---> Package ntp-doc.noarch 0:4.2.6p5-12.el6.centos.2 will be installed
---> Package ntpdate.x86_64 0:4.2.6p5-12.el6.centos.2 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================================================
 Package                              Arch                                Version                                               Repository                         Size
========================================================================================================================================================================
Installing:
 ntp                                  x86_64                              4.2.6p5-12.el6.centos.2                               base                              600 k
 ntp-doc                              noarch                              4.2.6p5-12.el6.centos.2                               base                              1.0 M
 ntpdate                              x86_64                              4.2.6p5-12.el6.centos.2                               base                               79 k

Transaction Summary
========================================================================================================================================================================
Install       3 Package(s)

Total download size: 1.7 M
Installed size: 3.4 M
Is this ok [y/N]: y
Downloading Packages:
(1/3): ntp-4.2.6p5-12.el6.centos.2.x86_64.rpm                                                                                                    | 600 kB     00:00
(2/3): ntp-doc-4.2.6p5-12.el6.centos.2.noarch.rpm                                                                                                | 1.0 MB     00:00
(3/3): ntpdate-4.2.6p5-12.el6.centos.2.x86_64.rpm                                                                                                |  79 kB     00:00
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                   2.8 MB/s | 1.7 MB     00:00
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : ntpdate-4.2.6p5-12.el6.centos.2.x86_64                                                                                                               1/3
  Installing : ntp-4.2.6p5-12.el6.centos.2.x86_64                                                                                                                   2/3
  Installing : ntp-doc-4.2.6p5-12.el6.centos.2.noarch                                                                                                               3/3
  Verifying  : ntp-doc-4.2.6p5-12.el6.centos.2.noarch                                                                                                               1/3
  Verifying  : ntpdate-4.2.6p5-12.el6.centos.2.x86_64                                                                                                               2/3
  Verifying  : ntp-4.2.6p5-12.el6.centos.2.x86_64                                                                                                                   3/3

Installed:
  ntp.x86_64 0:4.2.6p5-12.el6.centos.2                 ntp-doc.noarch 0:4.2.6p5-12.el6.centos.2                 ntpdate.x86_64 0:4.2.6p5-12.el6.centos.2

Complete!
```

```
[gianbo@gianbo01 ~]$ sudo chkconfig ntpd on
[gianbo@gianbo01 ~]$ sudo service ntpd start
Starting ntpd:                                             [  OK  ]

```
