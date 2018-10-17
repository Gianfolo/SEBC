- What is ubertask optimization?

It's a setting within Yarn configuration that allow to run "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.

- Where in CM is the Kerberos Security Realm value displayed?

It's displayed within the cluster configuration (Administration -> Settings): the setting name is "Kerberos Security Realm".

- Which CDH service(s) host a property for enabling Kerberos authentication?

HDFS, Hive, Hue, Oozie, YARN, ZooKeeper, Cloudera Management Service

- How do you upgrade the CM agents?

As stated on this page https://www.cloudera.com/documentation/enterprise/upgrade/topics/ug_cm_upgrade_agent.html, the upgrade operation can be done in two ways:
1. Use the "Upgrade Wizard" on the CM. On my cluster the URL is: http://gianbo01.northeurope.cloudapp.azure.com:7180/cmf/upgrade-wizard/welcome
2. Upgrade the Agents using the Command Line

- Give the tsquery statement used to chart Hue's CPU utilization?

select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName=Hue

- Name all the roles that make up the Hive service

Hive Metastore Server
HiveServer2
Gateway

- What steps must be completed before integrating Cloudera Manager with Kerberos?

As the CM wizard explains, these are the steps that must be completed before integrating Cloudera Manager with Kerberos:
```
Before using the wizard, ensure that you have performed the following steps:
- Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.

- The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.

- OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.

- Cloudera Manager needs an account that has permissions to create other accounts in the KDC.
```

