- The full teragen command
```
[raffles@mambo02 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=6 -Ddfs.block.size=33554432 51200000 /user/raffles/tgen512
18/10/19 05:05:13 INFO client.RMProxy: Connecting to ResourceManager at mambo01.northeurope.cloudapp.azure.com/10.0.1.4:8032
18/10/19 05:05:14 INFO terasort.TeraGen: Generating 51200000 using 6
18/10/19 05:05:14 INFO mapreduce.JobSubmitter: number of splits:6
18/10/19 05:05:14 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
18/10/19 05:05:14 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/10/19 05:05:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539938776097_0001
18/10/19 05:05:15 INFO impl.YarnClientImpl: Submitted application application_1539938776097_0001
18/10/19 05:05:15 INFO mapreduce.Job: The url to track the job: http://mambo01.northeurope.cloudapp.azure.com:8088/proxy/application_1539938776097_0001/
18/10/19 05:05:15 INFO mapreduce.Job: Running job: job_1539938776097_0001
18/10/19 05:05:23 INFO mapreduce.Job: Job job_1539938776097_0001 running in uber mode : false
18/10/19 05:05:23 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 05:05:40 INFO mapreduce.Job:  map 17% reduce 0%
18/10/19 05:05:41 INFO mapreduce.Job:  map 35% reduce 0%
18/10/19 05:05:43 INFO mapreduce.Job:  map 44% reduce 0%
18/10/19 05:05:44 INFO mapreduce.Job:  map 58% reduce 0%
18/10/19 05:05:47 INFO mapreduce.Job:  map 64% reduce 0%
18/10/19 05:05:52 INFO mapreduce.Job:  map 70% reduce 0%
18/10/19 05:05:53 INFO mapreduce.Job:  map 76% reduce 0%
18/10/19 05:05:57 INFO mapreduce.Job:  map 78% reduce 0%
18/10/19 05:05:58 INFO mapreduce.Job:  map 86% reduce 0%
18/10/19 05:06:04 INFO mapreduce.Job:  map 91% reduce 0%
18/10/19 05:06:06 INFO mapreduce.Job:  map 94% reduce 0%
18/10/19 05:06:07 INFO mapreduce.Job:  map 100% reduce 0%
18/10/19 05:06:08 INFO mapreduce.Job: Job job_1539938776097_0001 completed successfully
18/10/19 05:06:08 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=897612
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=511
                HDFS: Number of bytes written=5120000000
                HDFS: Number of read operations=24
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters
                Launched map tasks=6
                Other local map tasks=6
                Total time spent by all maps in occupied slots (ms)=205636
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=205636
                Total vcore-milliseconds taken by all map tasks=205636
                Total megabyte-milliseconds taken by all map tasks=210571264
        Map-Reduce Framework
                Map input records=51200000
                Map output records=51200000
                Input split bytes=511
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1179
                CPU time spent (ms)=115270
                Physical memory (bytes) snapshot=2299043840
                Virtual memory (bytes) snapshot=16656932864
                Total committed heap usage (bytes)=2270691328
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=109963291816450258
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=5120000000
```

- The output of the time command
```
real    0m57.369s
user    0m8.286s
sys     0m0.515s
```

- The command and output of hdfs dfs -ls /user/raffles/tgen512
```
[raffles@mambo02 ~]$ hdfs dfs -ls /user/raffles/tgen512
Found 7 items
-rw-r--r--   3 raffles shops          0 2018-10-19 05:06 /user/raffles/tgen512/_SUCCESS
-rw-r--r--   3 raffles shops  853333400 2018-10-19 05:06 /user/raffles/tgen512/part-m-00000
-rw-r--r--   3 raffles shops  853333300 2018-10-19 05:06 /user/raffles/tgen512/part-m-00001
-rw-r--r--   3 raffles shops  853333300 2018-10-19 05:06 /user/raffles/tgen512/part-m-00002
-rw-r--r--   3 raffles shops  853333400 2018-10-19 05:05 /user/raffles/tgen512/part-m-00003
-rw-r--r--   3 raffles shops  853333300 2018-10-19 05:05 /user/raffles/tgen512/part-m-00004
-rw-r--r--   3 raffles shops  853333300 2018-10-19 05:05 /user/raffles/tgen512/part-m-00005
```

- Show how many blocks are associated with this directory

There are 156 block within the directory
```
[raffles@mambo02 ~]$ hadoop fsck /user/raffles/tgen512
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://mambo01.northeurope.cloudapp.azure.com:50070/fsck?ugi=raffles&path=%2Fuser%2Fraffles%2Ftgen512
FSCK started by raffles (auth:SIMPLE) from /10.0.1.5 for path /user/raffles/tgen512 at Fri Oct 19 05:10:34 EDT 2018
.......Status: HEALTHY
 Total size:    5120000000 B
 Total dirs:    1
 Total files:   7
 Total symlinks:                0
 Total blocks (validated):      156 (avg. block size 32820512 B)
 Minimally replicated blocks:   156 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Fri Oct 19 05:10:34 EDT 2018 in 1 milliseconds


The filesystem under path '/user/raffles/tgen512' is HEALTHY
```
