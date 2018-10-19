- List the cloud provider you are using (AWS, GCE, Azure, other)
Azure

- List the Linux release you have chosen
CentOS 6.10

- Show that the disk space on each node is at least 30 GB
```
[gianbo@mambo01 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        49G  1.7G   45G   4% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
/dev/sda1       240M   70M  159M  31% /boot
/dev/sdb1        99G  2.1G   92G   3% /mnt/resource

[gianbo@mambo02 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        49G  1.7G   45G   4% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
/dev/sda1       240M   70M  159M  31% /boot
/dev/sdb1        99G  2.1G   92G   3% /mnt/resource
/dev/sdc1        50G   52M   49G   1% /data/1
/dev/sdc2        50G   52M   49G   1% /data/2

[gianbo@mambo03 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        49G  1.7G   45G   4% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
/dev/sda1       240M   70M  159M  31% /boot
/dev/sdb1        99G  2.1G   92G   3% /mnt/resource
/dev/sdc1        50G   52M   49G   1% /data/1
/dev/sdc2        50G   52M   49G   1% /data/2

[gianbo@mambo04 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        49G  1.7G   45G   4% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
/dev/sda1       240M   70M  159M  31% /boot
/dev/sdb1        99G  2.1G   92G   3% /mnt/resource
/dev/sdc1        50G   52M   49G   1% /data/1
/dev/sdc2        50G   52M   49G   1% /data/2

[gianbo@mambo05 ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        49G  1.7G   45G   4% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
/dev/sda1       240M   70M  159M  31% /boot
/dev/sdb1        99G  2.1G   92G   3% /mnt/resource
/dev/sdc1        50G   52M   49G   1% /data/1
/dev/sdc2        50G   52M   49G   1% /data/2
```

- List the command and output for yum repolist enabled
```
[gianbo@mambo01 ~]$ sudo yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
base                                                                                                                                             | 3.7 kB     00:00
extras                                                                                                                                           | 3.4 kB     00:00
mysql-connectors-community                                                                                                                       | 2.5 kB     00:00
mysql-tools-community                                                                                                                            | 2.5 kB     00:00
mysql80-community                                                                                                                                | 2.5 kB     00:00
openlogic                                                                                                                                        | 2.9 kB     00:00
updates                                                                                                                                          | 3.4 kB     00:00
repo id                                                                   repo name                                                                               status
base                                                                      CentOS-6 - Base                                                                         6,713
extras                                                                    CentOS-6 - Extras                                                                          33
mysql-connectors-community                                                MySQL Connectors Community                                                                 59
mysql-tools-community                                                     MySQL Tools Community                                                                      65
mysql80-community                                                         MySQL 8.0 Community Server                                                                 29
openlogic                                                                 CentOS-6 - openlogic packages for x86_64                                                  104
updates                                                                   CentOS-6 - Updates                                                                        205
repolist: 7,208
```

- List the /etc/passwd entries for raffles and fullerton in your setup file
```
raffles:x:2000:2000::/home/raffles:/bin/bash
fullerton:x:3000:3000::/home/fullerton:/bin/bash
```

- List the /etc/group entries for hotels and shops in your setup file
```
hotels:x:3000:
shops:x:2000:
```
