- Command and output for hdfs dfs -ls /user
```
[gianbo@mambo02 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - fullerton hotels          0 2018-10-19 04:50 /user/fullerton
drwxrwxrwx   - mapred    hadoop          0 2018-10-19 04:46 /user/history
drwxrwxr-t   - hive      hive            0 2018-10-19 04:47 /user/hive
drwxrwxr-x   - hue       hue             0 2018-10-19 04:47 /user/hue
drwxrwxr-x   - oozie     oozie           0 2018-10-19 04:47 /user/oozie
drwxr-xr-x   - raffles   shops           0 2018-10-19 04:49 /user/raffles
```

- The output from the CM API call ../api/v14/hosts
```
{
  "items" : [ {
    "hostId" : "b7812f9a-64fd-4cf2-b674-d4270bb741b8",
    "ipAddress" : "10.0.1.4",
    "hostname" : "mambo01.northeurope.cloudapp.azure.com",
    "rackId" : "/default",
    "hostUrl" : "http://mambo02.northeurope.cloudapp.azure.com:7180/cmf/hostRedirect/b7812f9a-64fd-4cf2-b674-d4270bb741b8",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16846589952
  }, {
    "hostId" : "bf8f7d3d-b373-4088-ac63-f093fdddd6da",
    "ipAddress" : "10.0.1.5",
    "hostname" : "mambo02.northeurope.cloudapp.azure.com",
    "rackId" : "/default",
    "hostUrl" : "http://mambo02.northeurope.cloudapp.azure.com:7180/cmf/hostRedirect/bf8f7d3d-b373-4088-ac63-f093fdddd6da",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16846589952
  }, {
    "hostId" : "34a68f04-4565-46c9-bcfe-25a20ed65213",
    "ipAddress" : "10.0.1.6",
    "hostname" : "mambo03.northeurope.cloudapp.azure.com",
    "rackId" : "/default",
    "hostUrl" : "http://mambo02.northeurope.cloudapp.azure.com:7180/cmf/hostRedirect/34a68f04-4565-46c9-bcfe-25a20ed65213",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16846589952
  }, {
    "hostId" : "788ced5a-cb5b-439f-83e0-328803a83f61",
    "ipAddress" : "10.0.1.7",
    "hostname" : "mambo04.northeurope.cloudapp.azure.com",
    "rackId" : "/default",
    "hostUrl" : "http://mambo02.northeurope.cloudapp.azure.com:7180/cmf/hostRedirect/788ced5a-cb5b-439f-83e0-328803a83f61",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16846589952
  }, {
    "hostId" : "b95710fe-ee36-445f-bb68-a4f434308c0f",
    "ipAddress" : "10.0.1.8",
    "hostname" : "mambo05.northeurope.cloudapp.azure.com",
    "rackId" : "/default",
    "hostUrl" : "http://mambo02.northeurope.cloudapp.azure.com:7180/cmf/hostRedirect/b95710fe-ee36-445f-bb68-a4f434308c0f",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16846589952
  } ]
}
```
