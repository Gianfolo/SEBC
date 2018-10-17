- Stop Hive service
```
[gianbo@gianbo01 ~]$ curl -X POST -u gianfolo:cloudera http://gianbo01.northeurope.cloudapp.azure.com:7180/api/v1/clusters/gianfolo/services/hive/commands/stop
{
  "id" : 498,
  "name" : "Stop",
  "startTime" : "2018-10-17T08:58:17.563Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

- Start Hive service
```
[gianbo@gianbo01 ~]$ curl -X POST -u gianfolo:cloudera http://gianbo01.northeurope.cloudapp.azure.com:7180/api/v1/clusters/gianfolo/services/hive/commands/start
{
  "id" : 502,
  "name" : "Start",
  "startTime" : "2018-10-17T08:59:38.603Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

- Check the current state of your Hive service
```
[gianbo@gianbo01 ~]$ curl -u gianfolo:cloudera http://gianbo01.northeurope.cloudapp.azure.com:7180/api/v1/clusters/gianfolo/services/hive
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://gianbo01:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false
```
