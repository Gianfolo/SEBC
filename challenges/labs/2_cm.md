- List the command and output of ls /etc/yum.repos.d in challenges/labs/2_cm.md
```
[gianbo@mambo02 ~]$ ls /etc/yum.repos.d
CentOS-Base.repo       CentOS-fasttrack.repo  CentOS-Vault.repo      mysql-community.repo         OpenLogic.repo
CentOS-Debuginfo.repo  CentOS-Media.repo      cloudera-manager.repo  mysql-community-source.repo
```
- Use the scm_prepare_database.sh script to write your db.properties file
```
[root@mambo02 ~]# /usr/share/cmf/schema/scm_prepare_database.sh -h mambo01.northeurope.cloudapp.azure.com mysql scm scm
Enter SCM password:
JAVA_HOME=/usr/local/jdk18
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/local/jdk18/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
Fri Oct 19 04:01:29 EDT 2018 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
[2018-10-19 04:01:30,569] INFO     0[main] - com.cloudera.enterprise.dbutil.DbCommandExecutor.testDbConnection(DbCommandExecutor.java) - Successfully connected to database.
All done, your SCM database is configured correctly!
```
