- Verify user privileges
```
[gianbo@gianbo01 ~]$ kinit gianfolo@HADOOP.COM
Password for gianfolo@HADOOP.COM:
[gianbo@gianbo01 ~]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181018043838_532dc295-7df0-44ca-b5ba-5376084e4b2a): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018043838_532dc295-7df0-44ca-b5ba-5376084e4b2a); Time taken: 0.811 seconds
INFO  : Executing command(queryId=hive_20181018043838_532dc295-7df0-44ca-b5ba-5376084e4b2a): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018043838_532dc295-7df0-44ca-b5ba-5376084e4b2a); Time taken: 0.337 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.649 seconds)
```

- Create a Sentry role with full authorization
```
0: jdbc:hive2://localhost:10000/default> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181018043939_e91fe62f-a169-4355-b303-53802f1fbe6c): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018043939_e91fe62f-a169-4355-b303-53802f1fbe6c); Time taken: 0.082 seconds
INFO  : Executing command(queryId=hive_20181018043939_e91fe62f-a169-4355-b303-53802f1fbe6c): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018043939_e91fe62f-a169-4355-b303-53802f1fbe6c); Time taken: 0.387 seconds
INFO  : OK
No rows affected (0.484 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181018044040_1689ab50-b906-47a9-ae90-c9cd9644c31f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018044040_1689ab50-b906-47a9-ae90-c9cd9644c31f); Time taken: 0.159 seconds
INFO  : Executing command(queryId=hive_20181018044040_1689ab50-b906-47a9-ae90-c9cd9644c31f): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018044040_1689ab50-b906-47a9-ae90-c9cd9644c31f); Time taken: 0.14 seconds
INFO  : OK
No rows affected (0.312 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE sentry_admin TO GROUP gianfolo;
INFO  : Compiling command(queryId=hive_20181018044040_c0c67b86-725a-4dc9-a100-430f8c1b4b9d): GRANT ROLE sentry_admin TO GROUP gianfolo
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018044040_c0c67b86-725a-4dc9-a100-430f8c1b4b9d); Time taken: 0.074 seconds
INFO  : Executing command(queryId=hive_20181018044040_c0c67b86-725a-4dc9-a100-430f8c1b4b9d): GRANT ROLE sentry_admin TO GROUP gianfolo
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018044040_c0c67b86-725a-4dc9-a100-430f8c1b4b9d); Time taken: 0.114 seconds
INFO  : OK
No rows affected (0.203 seconds)
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181018044040_bf0c8d2b-d45d-4280-99c8-b9a78de2a70a): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018044040_bf0c8d2b-d45d-4280-99c8-b9a78de2a70a); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20181018044040_bf0c8d2b-d45d-4280-99c8-b9a78de2a70a): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018044040_bf0c8d2b-d45d-4280-99c8-b9a78de2a70a); Time taken: 0.124 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.271 seconds)
```

- Create additional test users
```
[gianbo@gianbo01 ~]$ sudo groupadd selector
[gianbo@gianbo01 ~]$ sudo groupadd inserters
[gianbo@gianbo01 ~]$ sudo useradd -u 1100 -g selector george
[gianbo@gianbo01 ~]$ sudo useradd -u 1200 -g inserters ferdinand

[gianbo@gianbo01 ~]$ kinit admin/admin
Password for admin/admin@HADOOP.COM:
[gianbo@gianbo01 ~]$ kadmin -q 'add_principal george'
Authenticating as principal admin/admin@HADOOP.COM with password.
Password for admin/admin@HADOOP.COM:
WARNING: no policy specified for george@HADOOP.COM; defaulting to no policy
Enter password for principal "george@HADOOP.COM":
Re-enter password for principal "george@HADOOP.COM":
Principal "george@HADOOP.COM" created.

[gianbo@gianbo01 ~]$ kadmin -q 'add_principal ferdinand'
Authenticating as principal admin/admin@HADOOP.COM with password.
Password for admin/admin@HADOOP.COM:
WARNING: no policy specified for ferdinand@HADOOP.COM; defaulting to no policy
Enter password for principal "ferdinand@HADOOP.COM":
Re-enter password for principal "ferdinand@HADOOP.COM":
Principal "ferdinand@HADOOP.COM" created.
```

- Create test roles
```
[gianbo@gianbo01 ~]$ kinit gianfolo@HADOOP.COM
Password for gianfolo@HADOOP.COM:
[gianbo@gianbo01 ~]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20181018045151_dd0aef8b-8b70-48c3-8baa-4bed486996d3): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045151_dd0aef8b-8b70-48c3-8baa-4bed486996d3); Time taken: 0.081 seconds
INFO  : Executing command(queryId=hive_20181018045151_dd0aef8b-8b70-48c3-8baa-4bed486996d3): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045151_dd0aef8b-8b70-48c3-8baa-4bed486996d3); Time taken: 0.06 seconds
INFO  : OK
No rows affected (0.222 seconds)
0: jdbc:hive2://localhost:10000/default> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20181018045252_994c77de-43cd-42a6-b818-1fb2f65a6ecc): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045252_994c77de-43cd-42a6-b818-1fb2f65a6ecc); Time taken: 0.114 seconds
INFO  : Executing command(queryId=hive_20181018045252_994c77de-43cd-42a6-b818-1fb2f65a6ecc): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045252_994c77de-43cd-42a6-b818-1fb2f65a6ecc); Time taken: 0.04 seconds
INFO  : OK
No rows affected (0.168 seconds)
```

- Grant read privilege for all tables to reads
```
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20181018045353_b9880801-0963-4b67-86e4-abb8c6405044): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045353_b9880801-0963-4b67-86e4-abb8c6405044); Time taken: 0.08 seconds
INFO  : Executing command(queryId=hive_20181018045353_b9880801-0963-4b67-86e4-abb8c6405044): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045353_b9880801-0963-4b67-86e4-abb8c6405044); Time taken: 0.049 seconds
INFO  : OK
No rows affected (0.141 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20181018045353_4ebf44ce-4a11-48e7-99ca-9b80db9c78ae): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045353_4ebf44ce-4a11-48e7-99ca-9b80db9c78ae); Time taken: 0.091 seconds
INFO  : Executing command(queryId=hive_20181018045353_4ebf44ce-4a11-48e7-99ca-9b80db9c78ae): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045353_4ebf44ce-4a11-48e7-99ca-9b80db9c78ae); Time taken: 0.049 seconds
INFO  : OK
No rows affected (0.155 seconds)
```

- Grant read privilege for default.sample07 only to 'writes'
```
0: jdbc:hive2://localhost:10000/default> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20181018045454_67c6b004-ee54-4b4c-aa74-aeaa736dfc7d): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045454_67c6b004-ee54-4b4c-aa74-aeaa736dfc7d); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20181018045454_67c6b004-ee54-4b4c-aa74-aeaa736dfc7d): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045454_67c6b004-ee54-4b4c-aa74-aeaa736dfc7d); Time taken: 0.049 seconds
INFO  : OK
No rows affected (0.202 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20181018045454_bf9e136b-bae4-4ce5-b6d2-d033bbb16a6f): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045454_bf9e136b-bae4-4ce5-b6d2-d033bbb16a6f); Time taken: 0.074 seconds
INFO  : Executing command(queryId=hive_20181018045454_bf9e136b-bae4-4ce5-b6d2-d033bbb16a6f): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045454_bf9e136b-bae4-4ce5-b6d2-d033bbb16a6f); Time taken: 0.061 seconds
INFO  : OK
No rows affected (0.146 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20181018045454_1d9dad93-b672-44b1-8cc0-7989ec5c6bcf): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045454_1d9dad93-b672-44b1-8cc0-7989ec5c6bcf); Time taken: 0.116 seconds
INFO  : Executing command(queryId=hive_20181018045454_1d9dad93-b672-44b1-8cc0-7989ec5c6bcf): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045454_1d9dad93-b672-44b1-8cc0-7989ec5c6bcf); Time taken: 0.044 seconds
INFO  : OK
No rows affected (0.171 seconds)
```

- kinit as george, then login to beeline
```
[gianbo@gianbo01 ~]$ kinit george
Password for george@HADOOP.COM:
[gianbo@gianbo01 ~]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181018045555_0bcc15f5-3d55-407e-822d-403fdb17fd2c): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045555_0bcc15f5-3d55-407e-822d-403fdb17fd2c); Time taken: 0.074 seconds
INFO  : Executing command(queryId=hive_20181018045555_0bcc15f5-3d55-407e-822d-403fdb17fd2c): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045555_0bcc15f5-3d55-407e-822d-403fdb17fd2c); Time taken: 0.13 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.339 seconds)
0: jdbc:hive2://localhost:10000/default> Closing: 0: jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
[gianbo@gianbo01 ~]$
[gianbo@gianbo01 ~]$ kinit ferdinand
Password for ferdinand@HADOOP.COM:
[gianbo@gianbo01 ~]$ beeline
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181018045656_67fa62b0-e346-4a07-a358-305eca47c982): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018045656_67fa62b0-e346-4a07-a358-305eca47c982); Time taken: 0.094 seconds
INFO  : Executing command(queryId=hive_20181018045656_67fa62b0-e346-4a07-a358-305eca47c982): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018045656_67fa62b0-e346-4a07-a358-305eca47c982); Time taken: 0.127 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.338 seconds)
0: jdbc:hive2://localhost:10000/default> Closing: 0: jdbc:hive2://localhost:10000/default;principal=hive/gianbo01.northeurope.cloudapp.azure.com@HADOOP.COM
[gianbo@gianbo01 ~]$
```
