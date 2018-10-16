- Create an end-user Linux account named with your GitHub handle
```
[gianbo@gianbo05 ~]$ sudo useradd gianfolo
[gianbo@gianbo05 ~]$ sudo passwd gianfolo
Changing password for user gianfolo.
New password:
BAD PASSWORD: it is based on a dictionary word
Retype new password:
passwd: all authentication tokens updated successfully.
```

- Create a home HDFS directory for this user as well

Created the home HDFS folder and assign to user/group gianfolo
```
[gianbo@gianbo01 ~]$ hdfs dfs -mkdir /user/gianfolo
[gianbo@gianbo01 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - hdfs   supergroup          0 2018-10-16 07:17 /user/gianfolo
drwx------   - hdfs   supergroup          0 2018-10-16 06:21 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2018-10-15 14:33 /user/history
drwxrwxr-t   - hive   hive                0 2018-10-15 14:34 /user/hive
drwxrwxr-x   - hue    hue                 0 2018-10-15 14:34 /user/hue
drwxrwxr-x   - oozie  oozie               0 2018-10-15 14:34 /user/oozie

[gianbo@gianbo01 ~]$ export HADOOP_USER_NAME=hdfs
[gianbo@gianbo01 ~]$ hdfs dfs -chown -R gianfolo:gianfolo /user/gianfolo
[gianbo@gianbo01 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - gianfolo gianfolo            0 2018-10-16 07:17 /user/gianfolo
drwx------   - hdfs     supergroup          0 2018-10-16 06:21 /user/hdfs
drwxrwxrwx   - mapred   hadoop              0 2018-10-15 14:33 /user/history
drwxrwxr-t   - hive     hive                0 2018-10-15 14:34 /user/hive
drwxrwxr-x   - hue      hue                 0 2018-10-15 14:34 /user/hue
drwxrwxr-x   - oozie    oozie               0 2018-10-15 14:34 /user/oozie
```

- Run the following exercises as this user
```
[gianbo@gianbo01 ~]$ su gianfolo
Password:
[gianfolo@gianbo01 gianbo]$
```

- Create a 10 GB file using teragen
```
[gianfolo@gianbo01 gianbo]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -Ddfs.block.size=33554432 104857600 /user/gianfolo/unsorted
18/10/16 08:09:54 INFO client.RMProxy: Connecting to ResourceManager at gianbo01/10.0.0.4:8032
18/10/16 08:09:55 INFO terasort.TeraGen: Generating 104857600 using 4
18/10/16 08:09:55 INFO mapreduce.JobSubmitter: number of splits:4
18/10/16 08:09:55 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/10/16 08:09:55 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
18/10/16 08:09:56 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539681810665_0014
18/10/16 08:09:56 INFO impl.YarnClientImpl: Submitted application application_1539681810665_0014
18/10/16 08:09:56 INFO mapreduce.Job: The url to track the job: http://gianbo01:8088/proxy/application_1539681810665_0014/
18/10/16 08:09:56 INFO mapreduce.Job: Running job: job_1539681810665_0014
18/10/16 08:10:07 INFO mapreduce.Job: Job job_1539681810665_0014 running in uber mode : false
18/10/16 08:10:07 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 08:10:25 INFO mapreduce.Job:  map 8% reduce 0%
18/10/16 08:10:27 INFO mapreduce.Job:  map 13% reduce 0%
18/10/16 08:10:28 INFO mapreduce.Job:  map 23% reduce 0%
18/10/16 08:10:31 INFO mapreduce.Job:  map 26% reduce 0%
18/10/16 08:10:33 INFO mapreduce.Job:  map 29% reduce 0%
18/10/16 08:10:34 INFO mapreduce.Job:  map 34% reduce 0%
18/10/16 08:10:37 INFO mapreduce.Job:  map 37% reduce 0%
18/10/16 08:10:39 INFO mapreduce.Job:  map 39% reduce 0%
18/10/16 08:10:40 INFO mapreduce.Job:  map 44% reduce 0%
18/10/16 08:10:43 INFO mapreduce.Job:  map 47% reduce 0%
18/10/16 08:10:45 INFO mapreduce.Job:  map 49% reduce 0%
18/10/16 08:10:46 INFO mapreduce.Job:  map 53% reduce 0%
18/10/16 08:10:49 INFO mapreduce.Job:  map 56% reduce 0%
18/10/16 08:10:51 INFO mapreduce.Job:  map 58% reduce 0%
18/10/16 08:10:52 INFO mapreduce.Job:  map 63% reduce 0%
18/10/16 08:10:55 INFO mapreduce.Job:  map 65% reduce 0%
18/10/16 08:10:57 INFO mapreduce.Job:  map 67% reduce 0%
18/10/16 08:10:58 INFO mapreduce.Job:  map 71% reduce 0%
18/10/16 08:11:01 INFO mapreduce.Job:  map 73% reduce 0%
18/10/16 08:11:03 INFO mapreduce.Job:  map 74% reduce 0%
18/10/16 08:11:04 INFO mapreduce.Job:  map 76% reduce 0%
18/10/16 08:11:09 INFO mapreduce.Job:  map 77% reduce 0%
18/10/16 08:11:11 INFO mapreduce.Job:  map 78% reduce 0%
18/10/16 08:11:15 INFO mapreduce.Job:  map 80% reduce 0%
18/10/16 08:11:16 INFO mapreduce.Job:  map 84% reduce 0%
18/10/16 08:11:21 INFO mapreduce.Job:  map 86% reduce 0%
18/10/16 08:11:22 INFO mapreduce.Job:  map 90% reduce 0%
18/10/16 08:11:27 INFO mapreduce.Job:  map 91% reduce 0%
18/10/16 08:11:28 INFO mapreduce.Job:  map 94% reduce 0%
18/10/16 08:11:30 INFO mapreduce.Job:  map 95% reduce 0%
18/10/16 08:11:32 INFO mapreduce.Job:  map 97% reduce 0%
18/10/16 08:11:33 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 08:11:34 INFO mapreduce.Job: Job job_1539681810665_0014 completed successfully
18/10/16 08:11:34 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=590528
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=344
                HDFS: Number of bytes written=10485760000
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=308587
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=308587
                Total vcore-milliseconds taken by all map tasks=308587
                Total megabyte-milliseconds taken by all map tasks=315993088
        Map-Reduce Framework
                Map input records=104857600
                Map output records=104857600
                Input split bytes=344
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1551
                CPU time spent (ms)=181090
                Physical memory (bytes) snapshot=701841408
                Virtual memory (bytes) snapshot=6262984704
                Total committed heap usage (bytes)=962068480
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=225186913807133164
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=10485760000

real    1m42.530s
user    0m6.126s
sys     0m0.354s
```
The job required 1m42.530s.

- Run the terasort command on this file
```
[gianfolo@gianbo01 gianbo]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/gianfolo/unsorted /user/gianfolo/sorted
18/10/16 08:13:05 INFO terasort.TeraSort: starting
18/10/16 08:13:06 INFO input.FileInputFormat: Total input paths to process : 4
Spent 241ms computing base-splits.
Spent 7ms computing TeraScheduler splits.
Computing input splits took 249ms
Sampling 10 splits of 316
Making 8 from 100000 sampled records
Computing parititions took 1022ms
Spent 1273ms computing partitions.
18/10/16 08:13:07 INFO client.RMProxy: Connecting to ResourceManager at gianbo01/10.0.0.4:8032
18/10/16 08:13:08 INFO mapreduce.JobSubmitter: number of splits:316
18/10/16 08:13:08 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539681810665_0015
18/10/16 08:13:09 INFO impl.YarnClientImpl: Submitted application application_1539681810665_0015
18/10/16 08:13:09 INFO mapreduce.Job: The url to track the job: http://gianbo01:8088/proxy/application_1539681810665_0015/
18/10/16 08:13:09 INFO mapreduce.Job: Running job: job_1539681810665_0015
18/10/16 08:13:15 INFO mapreduce.Job: Job job_1539681810665_0015 running in uber mode : false
18/10/16 08:13:15 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 08:13:26 INFO mapreduce.Job:  map 1% reduce 0%
18/10/16 08:13:31 INFO mapreduce.Job:  map 2% reduce 0%
18/10/16 08:13:35 INFO mapreduce.Job:  map 3% reduce 0%
18/10/16 08:13:37 INFO mapreduce.Job:  map 5% reduce 0%
18/10/16 08:13:38 INFO mapreduce.Job:  map 6% reduce 0%
18/10/16 08:13:44 INFO mapreduce.Job:  map 7% reduce 0%
18/10/16 08:13:45 INFO mapreduce.Job:  map 8% reduce 0%
18/10/16 08:13:54 INFO mapreduce.Job:  map 9% reduce 0%
18/10/16 08:13:56 INFO mapreduce.Job:  map 10% reduce 0%
18/10/16 08:13:57 INFO mapreduce.Job:  map 11% reduce 0%
18/10/16 08:13:58 INFO mapreduce.Job:  map 12% reduce 0%
18/10/16 08:14:00 INFO mapreduce.Job:  map 13% reduce 0%
18/10/16 08:14:03 INFO mapreduce.Job:  map 14% reduce 0%
18/10/16 08:14:12 INFO mapreduce.Job:  map 15% reduce 0%
18/10/16 08:14:13 INFO mapreduce.Job:  map 16% reduce 0%
18/10/16 08:14:16 INFO mapreduce.Job:  map 17% reduce 0%
18/10/16 08:14:18 INFO mapreduce.Job:  map 18% reduce 0%
18/10/16 08:14:20 INFO mapreduce.Job:  map 19% reduce 0%
18/10/16 08:14:22 INFO mapreduce.Job:  map 20% reduce 0%
18/10/16 08:14:27 INFO mapreduce.Job:  map 21% reduce 0%
18/10/16 08:14:33 INFO mapreduce.Job:  map 22% reduce 0%
18/10/16 08:14:36 INFO mapreduce.Job:  map 23% reduce 0%
18/10/16 08:14:39 INFO mapreduce.Job:  map 25% reduce 0%
18/10/16 08:14:41 INFO mapreduce.Job:  map 26% reduce 0%
18/10/16 08:14:47 INFO mapreduce.Job:  map 27% reduce 0%
18/10/16 08:14:52 INFO mapreduce.Job:  map 28% reduce 0%
18/10/16 08:14:55 INFO mapreduce.Job:  map 29% reduce 0%
18/10/16 08:14:56 INFO mapreduce.Job:  map 30% reduce 0%
18/10/16 08:14:59 INFO mapreduce.Job:  map 31% reduce 0%
18/10/16 08:15:00 INFO mapreduce.Job:  map 32% reduce 0%
18/10/16 08:15:05 INFO mapreduce.Job:  map 33% reduce 0%
18/10/16 08:15:08 INFO mapreduce.Job:  map 34% reduce 0%
18/10/16 08:15:14 INFO mapreduce.Job:  map 35% reduce 0%
18/10/16 08:15:15 INFO mapreduce.Job:  map 36% reduce 0%
18/10/16 08:15:18 INFO mapreduce.Job:  map 37% reduce 0%
18/10/16 08:15:19 INFO mapreduce.Job:  map 38% reduce 0%
18/10/16 08:15:20 INFO mapreduce.Job:  map 39% reduce 0%
18/10/16 08:15:25 INFO mapreduce.Job:  map 40% reduce 0%
18/10/16 08:15:31 INFO mapreduce.Job:  map 41% reduce 0%
18/10/16 08:15:34 INFO mapreduce.Job:  map 42% reduce 0%
18/10/16 08:15:35 INFO mapreduce.Job:  map 43% reduce 0%
18/10/16 08:15:39 INFO mapreduce.Job:  map 44% reduce 0%
18/10/16 08:15:40 INFO mapreduce.Job:  map 45% reduce 0%
18/10/16 08:15:44 INFO mapreduce.Job:  map 46% reduce 0%
18/10/16 08:15:45 INFO mapreduce.Job:  map 47% reduce 0%
18/10/16 08:15:52 INFO mapreduce.Job:  map 48% reduce 0%
18/10/16 08:15:53 INFO mapreduce.Job:  map 49% reduce 0%
18/10/16 08:15:56 INFO mapreduce.Job:  map 50% reduce 0%
18/10/16 08:15:59 INFO mapreduce.Job:  map 51% reduce 0%
18/10/16 08:16:01 INFO mapreduce.Job:  map 52% reduce 0%
18/10/16 08:16:04 INFO mapreduce.Job:  map 53% reduce 0%
18/10/16 08:16:10 INFO mapreduce.Job:  map 54% reduce 0%
18/10/16 08:16:12 INFO mapreduce.Job:  map 55% reduce 0%
18/10/16 08:16:13 INFO mapreduce.Job:  map 56% reduce 0%
18/10/16 08:16:19 INFO mapreduce.Job:  map 57% reduce 0%
18/10/16 08:16:21 INFO mapreduce.Job:  map 58% reduce 0%
18/10/16 08:16:22 INFO mapreduce.Job:  map 59% reduce 0%
18/10/16 08:16:29 INFO mapreduce.Job:  map 60% reduce 0%
18/10/16 08:16:31 INFO mapreduce.Job:  map 61% reduce 0%
18/10/16 08:16:32 INFO mapreduce.Job:  map 62% reduce 0%
18/10/16 08:16:36 INFO mapreduce.Job:  map 63% reduce 0%
18/10/16 08:16:40 INFO mapreduce.Job:  map 64% reduce 0%
18/10/16 08:16:42 INFO mapreduce.Job:  map 65% reduce 0%
18/10/16 08:16:45 INFO mapreduce.Job:  map 66% reduce 0%
18/10/16 08:16:50 INFO mapreduce.Job:  map 67% reduce 0%
18/10/16 08:16:51 INFO mapreduce.Job:  map 68% reduce 0%
18/10/16 08:16:52 INFO mapreduce.Job:  map 69% reduce 0%
18/10/16 08:17:00 INFO mapreduce.Job:  map 70% reduce 0%
18/10/16 08:17:01 INFO mapreduce.Job:  map 71% reduce 0%
18/10/16 08:17:03 INFO mapreduce.Job:  map 72% reduce 0%
18/10/16 08:17:08 INFO mapreduce.Job:  map 73% reduce 0%
18/10/16 08:17:10 INFO mapreduce.Job:  map 74% reduce 0%
18/10/16 08:17:11 INFO mapreduce.Job:  map 75% reduce 0%
18/10/16 08:17:15 INFO mapreduce.Job:  map 76% reduce 0%
18/10/16 08:17:19 INFO mapreduce.Job:  map 77% reduce 0%
18/10/16 08:17:23 INFO mapreduce.Job:  map 78% reduce 0%
18/10/16 08:17:26 INFO mapreduce.Job:  map 79% reduce 0%
18/10/16 08:17:29 INFO mapreduce.Job:  map 81% reduce 0%
18/10/16 08:17:33 INFO mapreduce.Job:  map 82% reduce 0%
18/10/16 08:17:37 INFO mapreduce.Job:  map 83% reduce 0%
18/10/16 08:17:42 INFO mapreduce.Job:  map 84% reduce 0%
18/10/16 08:17:44 INFO mapreduce.Job:  map 85% reduce 0%
18/10/16 08:17:50 INFO mapreduce.Job:  map 86% reduce 0%
18/10/16 08:17:53 INFO mapreduce.Job:  map 86% reduce 3%
18/10/16 08:17:55 INFO mapreduce.Job:  map 86% reduce 9%
18/10/16 08:17:56 INFO mapreduce.Job:  map 86% reduce 10%
18/10/16 08:17:59 INFO mapreduce.Job:  map 86% reduce 11%
18/10/16 08:18:00 INFO mapreduce.Job:  map 86% reduce 17%
18/10/16 08:18:01 INFO mapreduce.Job:  map 86% reduce 20%
18/10/16 08:18:02 INFO mapreduce.Job:  map 87% reduce 21%
18/10/16 08:18:05 INFO mapreduce.Job:  map 88% reduce 21%
18/10/16 08:18:06 INFO mapreduce.Job:  map 88% reduce 22%
18/10/16 08:18:08 INFO mapreduce.Job:  map 88% reduce 23%
18/10/16 08:18:11 INFO mapreduce.Job:  map 89% reduce 23%
18/10/16 08:18:12 INFO mapreduce.Job:  map 89% reduce 24%
18/10/16 08:18:13 INFO mapreduce.Job:  map 89% reduce 26%
18/10/16 08:18:20 INFO mapreduce.Job:  map 90% reduce 26%
18/10/16 08:18:24 INFO mapreduce.Job:  map 91% reduce 26%
18/10/16 08:18:29 INFO mapreduce.Job:  map 92% reduce 26%
18/10/16 08:18:30 INFO mapreduce.Job:  map 92% reduce 27%
18/10/16 08:18:38 INFO mapreduce.Job:  map 93% reduce 27%
18/10/16 08:18:41 INFO mapreduce.Job:  map 94% reduce 27%
18/10/16 08:18:45 INFO mapreduce.Job:  map 95% reduce 27%
18/10/16 08:18:48 INFO mapreduce.Job:  map 95% reduce 28%
18/10/16 08:18:53 INFO mapreduce.Job:  map 96% reduce 28%
18/10/16 08:18:55 INFO mapreduce.Job:  map 97% reduce 28%
18/10/16 08:19:03 INFO mapreduce.Job:  map 98% reduce 28%
18/10/16 08:19:07 INFO mapreduce.Job:  map 99% reduce 29%
18/10/16 08:19:09 INFO mapreduce.Job:  map 100% reduce 29%
18/10/16 08:19:17 INFO mapreduce.Job:  map 100% reduce 33%
18/10/16 08:19:19 INFO mapreduce.Job:  map 100% reduce 41%
18/10/16 08:19:20 INFO mapreduce.Job:  map 100% reduce 49%
18/10/16 08:19:21 INFO mapreduce.Job:  map 100% reduce 52%
18/10/16 08:19:22 INFO mapreduce.Job:  map 100% reduce 57%
18/10/16 08:19:24 INFO mapreduce.Job:  map 100% reduce 58%
18/10/16 08:19:25 INFO mapreduce.Job:  map 100% reduce 60%
18/10/16 08:19:26 INFO mapreduce.Job:  map 100% reduce 62%
18/10/16 08:19:27 INFO mapreduce.Job:  map 100% reduce 66%
18/10/16 08:19:28 INFO mapreduce.Job:  map 100% reduce 67%
18/10/16 08:19:30 INFO mapreduce.Job:  map 100% reduce 68%
18/10/16 08:19:31 INFO mapreduce.Job:  map 100% reduce 70%
18/10/16 08:19:32 INFO mapreduce.Job:  map 100% reduce 71%
18/10/16 08:19:33 INFO mapreduce.Job:  map 100% reduce 73%
18/10/16 08:19:34 INFO mapreduce.Job:  map 100% reduce 74%
18/10/16 08:19:36 INFO mapreduce.Job:  map 100% reduce 75%
18/10/16 08:19:37 INFO mapreduce.Job:  map 100% reduce 77%
18/10/16 08:19:38 INFO mapreduce.Job:  map 100% reduce 79%
18/10/16 08:19:39 INFO mapreduce.Job:  map 100% reduce 82%
18/10/16 08:19:42 INFO mapreduce.Job:  map 100% reduce 83%
18/10/16 08:19:43 INFO mapreduce.Job:  map 100% reduce 84%
18/10/16 08:19:44 INFO mapreduce.Job:  map 100% reduce 86%
18/10/16 08:19:45 INFO mapreduce.Job:  map 100% reduce 90%
18/10/16 08:19:48 INFO mapreduce.Job:  map 100% reduce 91%
18/10/16 08:19:49 INFO mapreduce.Job:  map 100% reduce 92%
18/10/16 08:19:50 INFO mapreduce.Job:  map 100% reduce 93%
18/10/16 08:19:51 INFO mapreduce.Job:  map 100% reduce 94%
18/10/16 08:19:56 INFO mapreduce.Job:  map 100% reduce 95%
18/10/16 08:19:57 INFO mapreduce.Job:  map 100% reduce 97%
18/10/16 08:20:02 INFO mapreduce.Job:  map 100% reduce 98%
18/10/16 08:20:03 INFO mapreduce.Job:  map 100% reduce 99%
18/10/16 08:20:09 INFO mapreduce.Job:  map 100% reduce 100%
18/10/16 08:20:12 INFO mapreduce.Job: Job job_1539681810665_0015 completed successfully
18/10/16 08:20:12 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=4695728867
                FILE: Number of bytes written=9331387510
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=10485798236
                HDFS: Number of bytes written=10485760000
                HDFS: Number of read operations=972
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=16
        Job Counters
                Launched map tasks=316
                Launched reduce tasks=8
                Data-local map tasks=314
                Rack-local map tasks=2
                Total time spent by all maps in occupied slots (ms)=4256214
                Total time spent by all reduces in occupied slots (ms)=986690
                Total time spent by all map tasks (ms)=4256214
                Total time spent by all reduce tasks (ms)=986690
                Total vcore-milliseconds taken by all map tasks=4256214
                Total vcore-milliseconds taken by all reduce tasks=986690
                Total megabyte-milliseconds taken by all map tasks=4358363136
                Total megabyte-milliseconds taken by all reduce tasks=1010370560
        Map-Reduce Framework
                Map input records=104857600
                Map output records=104857600
                Map output bytes=10695475200
                Map output materialized bytes=4587293249
                Input split bytes=38236
                Combine input records=0
                Combine output records=0
                Reduce input groups=104857600
                Reduce shuffle bytes=4587293249
                Reduce input records=104857600
                Reduce output records=104857600
                Spilled Records=209715200
                Shuffled Maps =2528
                Failed Shuffles=0
                Merged Map outputs=2528
                GC time elapsed (ms)=53850
                CPU time spent (ms)=1690610
                Physical memory (bytes) snapshot=159124680704
                Virtual memory (bytes) snapshot=508299116544
                Total committed heap usage (bytes)=188086222848
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=10485760000
        File Output Format Counters
                Bytes Written=10485760000
18/10/16 08:20:12 INFO terasort.TeraSort: done

real    7m8.387s
user    0m10.329s
sys     0m0.604s
```
The job required 7m8.387s.

