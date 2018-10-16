- Use teragen to create a 500 MB file
```
[gianbo@gianbo01 ~]$ export HADOOP_USER_NAME=hdfs
[gianbo@gianbo01 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=1 5242880 /hdfs_lab/gianfolo/unsorted 2>&1 | tee teragen_$(date +'%Y%m%d_%H%M%S')
18/10/16 04:17:48 INFO client.RMProxy: Connecting to ResourceManager at gianbo01/10.0.0.4:8032
18/10/16 04:17:48 INFO terasort.TeraGen: Generating 5242880 using 1
18/10/16 04:17:49 INFO mapreduce.JobSubmitter: number of splits:1
18/10/16 04:17:49 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
18/10/16 04:17:49 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539628382687_0003
18/10/16 04:17:49 INFO impl.YarnClientImpl: Submitted application application_1539628382687_0003
18/10/16 04:17:49 INFO mapreduce.Job: The url to track the job: http://gianbo01:8088/proxy/application_1539628382687_0003/
18/10/16 04:17:49 INFO mapreduce.Job: Running job: job_1539628382687_0003
18/10/16 04:17:55 INFO mapreduce.Job: Job job_1539628382687_0003 running in uber mode : false
18/10/16 04:17:55 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 04:18:06 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 04:18:07 INFO mapreduce.Job: Job job_1539628382687_0003 completed successfully
18/10/16 04:18:07 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=147608
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=82
                HDFS: Number of bytes written=524288000
                HDFS: Number of read operations=4
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
        Job Counters
                Launched map tasks=1
                Other local map tasks=1
                Total time spent by all maps in occupied slots (ms)=9234
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=9234
                Total vcore-milliseconds taken by all map tasks=9234
                Total megabyte-milliseconds taken by all map tasks=9455616
        Map-Reduce Framework
                Map input records=5242880
                Map output records=5242880
                Input split bytes=82
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=83
                CPU time spent (ms)=10080
                Physical memory (bytes) snapshot=367841280
                Virtual memory (bytes) snapshot=1566564352
                Total committed heap usage (bytes)=412090368
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=11257830824958050
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=524288000
```

- Copy your partner's file to your target directory
We were forced to enable the HDFS property dfs.client.use.datanode.hostname otherwise the distcp try to use the internal IP of the secondary cluster.
```
[gianbo@gianbo01 ~]$ hadoop distcp -overwrite -m 4 hdfs://elephant1.westeurope.cloudapp.azure.com:8020/user/bdany70/unsorted/part-m-00000 hdfs://gianbo01:8020/hdfs_lab/bdany70
18/10/16 05:53:00 INFO tools.OptionsParser: parseChunkSize: blocksperchunk false
18/10/16 05:53:02 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=true, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=4, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://elephant1.westeurope.cloudapp.azure.com:8020/user/bdany70/unsorted/part-m-00000], targetPath=hdfs://gianbo01:8020/hdfs_lab/bdany70, targetPathExists=true, filtersFile='null', blocksPerChunk=0, copyBufferSize=8192}
18/10/16 05:53:02 INFO client.RMProxy: Connecting to ResourceManager at gianbo01/10.0.0.4:8032
18/10/16 05:53:02 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 1; dirCnt = 0
18/10/16 05:53:02 INFO tools.SimpleCopyListing: Build file listing completed.
18/10/16 05:53:02 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
18/10/16 05:53:02 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
18/10/16 05:53:03 INFO tools.DistCp: Number of paths in the copy list: 1
18/10/16 05:53:03 INFO tools.DistCp: Number of paths in the copy list: 1
18/10/16 05:53:03 INFO client.RMProxy: Connecting to ResourceManager at gianbo01/10.0.0.4:8032
18/10/16 05:53:03 INFO mapreduce.JobSubmitter: number of splits:1
18/10/16 05:53:04 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539681810665_0008
18/10/16 05:53:04 INFO impl.YarnClientImpl: Submitted application application_1539681810665_0008
18/10/16 05:53:04 INFO mapreduce.Job: The url to track the job: http://gianbo01:8088/proxy/application_1539681810665_0008/
18/10/16 05:53:04 INFO tools.DistCp: DistCp job-id: job_1539681810665_0008
18/10/16 05:53:04 INFO mapreduce.Job: Running job: job_1539681810665_0008
18/10/16 05:53:10 INFO mapreduce.Job: Job job_1539681810665_0008 running in uber mode : false
18/10/16 05:53:10 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 05:53:25 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 05:53:26 INFO mapreduce.Job: Job job_1539681810665_0008 completed successfully
18/10/16 05:53:26 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=151101
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=524288416
                HDFS: Number of bytes written=524288000
                HDFS: Number of read operations=17
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=4
        Job Counters
                Launched map tasks=1
                Other local map tasks=1
                Total time spent by all maps in occupied slots (ms)=13730
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=13730
                Total vcore-milliseconds taken by all map tasks=13730
                Total megabyte-milliseconds taken by all map tasks=14059520
        Map-Reduce Framework
                Map input records=1
                Map output records=0
                Input split bytes=115
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=105
                CPU time spent (ms)=7580
                Physical memory (bytes) snapshot=380686336
                Virtual memory (bytes) snapshot=1567617024
                Total committed heap usage (bytes)=448790528
        File Input Format Counters
                Bytes Read=301
        File Output Format Counters
                Bytes Written=0
        DistCp Counters
                Bytes Copied=524288000
                Bytes Expected=524288000
                Files Copied=1
```

- Browse the results
```
[gianbo@gianbo01 ~]$ hdfs fsck /hdfs_lab/bdany70/part-m-00000 -files -blocks
Connecting to namenode via http://gianbo01:50070/fsck?ugi=hdfs&files=1&blocks=1&path=%2Fhdfs_lab%2Fbdany70%2Fpart-m-00000
FSCK started by hdfs (auth:SIMPLE) from /10.0.0.4 for path /hdfs_lab/bdany70/part-m-00000 at Tue Oct 16 05:59:00 EDT 2018
/hdfs_lab/bdany70/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-2003137288-10.0.0.4-1539628319082:blk_1073743723_2899 len=134217728 Live_repl=3
1. BP-2003137288-10.0.0.4-1539628319082:blk_1073743724_2900 len=134217728 Live_repl=3
2. BP-2003137288-10.0.0.4-1539628319082:blk_1073743725_2901 len=134217728 Live_repl=3
3. BP-2003137288-10.0.0.4-1539628319082:blk_1073743726_2902 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue Oct 16 05:59:00 EDT 2018 in 2 milliseconds


The filesystem under path '/hdfs_lab/bdany70/part-m-00000' is HEALTHY

```
