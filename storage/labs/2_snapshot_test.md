- Create a precious directory in HDFS; copy the ZIP course file into it.
```
[gianfolo@gianbo01 gianbo]$ export HADOOP_USER_NAME=hdfs
[gianfolo@gianbo01 gianbo]$ hdfs dfs -mkdir /precious
[gianfolo@gianbo01 gianbo]$ hdfs dfs -copyFromLocal /tmp/SEBC-master.zip /precious
```

- Enable snapshots for precious

Done from the CM interface.

- Create a snapshot called sebc-hdfs-test

Done from the CM interface.

- Delete the directory
```
[gianfolo@gianbo01 gianbo]$ hdfs dfs -rm -R -skipTrash /precious
rm: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
```
The folder cannot be deleted.

- Delete the ZIP file
```
[gianfolo@gianbo01 gianbo]$ hdfs dfs -rm -skipTrash /precious/SEBC-master.zip
Deleted /precious/SEBC-master.zip
```

- Restore the deleted file
```
[gianfolo@gianbo01 gianbo]$ hdfs dfs -ls /precious/.snapshot/sebc-hdfs-test
Found 1 items
-rw-r--r--   3 hdfs supergroup    1720611 2018-10-16 08:51 /precious/.snapshot/sebc-hdfs-test/SEBC-master.zip
[gianfolo@gianbo01 gianbo]$ hdfs dfs -cp -ptopax /precious/.snapshot/sebc-hdfs-test/SEBC-master.zip /precious/
[gianfolo@gianbo01 gianbo]$ hdfs dfs -ls /precious/
Found 1 items
-rw-r--r--   3 hdfs supergroup    1720611 2018-10-16 08:51 /precious/SEBC-master.zip
```
