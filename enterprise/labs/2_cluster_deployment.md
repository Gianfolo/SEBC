```
{
  "timestamp" : "2018-10-17T08:43:32.960Z",
  "clusters" : [ {
    "name" : "gianfolo",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "602931200"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "602931200"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3651613491"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "614"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "gianbo01"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "ABCD1_metastore"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-553818b2fdbeaf0263c6b9f579d79394",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-6e44b8542c4728bcaa2201162e65bc2b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f0718492-da6c-458d-b578-8e27c1a2f43b"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-ae1b426093b94c518ee4d4271fe7596b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "328f89a6-bbe4-4e6e-b8d7-08d2747254f6"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "atk27swbp1crvffnnjhyco62q"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2maowpj8dqd8bc6pl13tuxoe1"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "602931200"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9ikr7c7fjyrklkq3585pcgzag"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-553818b2fdbeaf0263c6b9f579d79394",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dsbhqgxw19j4k8yba2bc3aqae"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2nlw0y0xlv7j3g1fgwclhsp5f"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "gianbo01"
        }, {
          "name" : "database_password",
          "value" : "ABCD1_hue"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-0815ab40a03037e73c5c91e2688b22f1"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_LOAD_BALANCER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "HUE_LOAD_BALANCER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "u2j8scre5y0donpfb10hdhlk"
          } ]
        }
      }, {
        "name" : "hue-HUE_SERVER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "navmetadataserver_cmdb_password",
            "value" : "34efd2d9-e152-4398-86f2-dc79c1ea9992"
          }, {
            "name" : "role_jceks_password",
            "value" : "7yu5xhv42epxss1a1u9drbt0g"
          }, {
            "name" : "secret_key",
            "value" : "cMEck30a1ZwsQyy09AxDKqGGVGi2fi"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "gianbo01"
          }, {
            "name" : "oozie_database_password",
            "value" : "ABCD1_oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "602931200"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "evyi4leimazxddupxj2ug6cf4"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "3"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "602931200"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/data/1/yarn/nm,/data/2/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/data/yarn/container-logs,/mnt/resource/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "6094"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "602931200"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "6094"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "7HCSNbXaf9tDrKdTumKxfdSrLFzCsW"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ao1i605vncjorlt0j9gd0vhb7"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6jjrm8p25lrwhzd4jht5afgr5"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-553818b2fdbeaf0263c6b9f579d79394",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ekgudce6d8b2hkxtck6ckcyvi"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-6e44b8542c4728bcaa2201162e65bc2b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "f0718492-da6c-458d-b578-8e27c1a2f43b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "oxyfvxkornvbbfwpp46etrc5"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-ae1b426093b94c518ee4d4271fe7596b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "328f89a6-bbe4-4e6e-b8d7-08d2747254f6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eu64tccgki33gbgsdmlr21ek5"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "59"
          }, {
            "name" : "role_jceks_password",
            "value" : "9lye3ahmm09dum4t5k6lnk96d"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "602931200"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/data/1/dfs/dn,/data/2/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "10555378483"
          }, {
            "name" : "dfs_datanode_failed_volumes_tolerated",
            "value" : "1"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/data/1/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/data/1/dfs/nn,/data/2/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "602931200"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/data/1/dfs/snn,/data/2/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "602931200"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_client_use_datanode_hostname",
          "value" : "true"
        }, {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "QFsfFsJSasbY0oo9ogwPGGYkhStsQU"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "nEtrpp0QrDS8ZKx7l0QLeAOnpHo60r"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "GJEOq6TG2IjN4QbFIN9uy9qq7VE4Zs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6q9y47progsmrh2z5ab00n0xs"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-553818b2fdbeaf0263c6b9f579d79394",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "d8rbr6hdm8l22501s2n9kjveh"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-6e44b8542c4728bcaa2201162e65bc2b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "f0718492-da6c-458d-b578-8e27c1a2f43b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3bjv1kyok6an00e5jbz5luw2j"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-ae1b426093b94c518ee4d4271fe7596b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "328f89a6-bbe4-4e6e-b8d7-08d2747254f6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "k6gafw4p8mp9cb2p92rie2q1"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9sf9yoyj5ezzhi0qodzpfm94e"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "awenqegk2958jrfwe6nyqrp42"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cst3zokcba191fjhopwndeqat"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "et0l601bog5apai8hhhdkjidf"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-553818b2fdbeaf0263c6b9f579d79394",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6k0jmzpfywh90gedmg8gb1lxx"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "adwg2saak49ax292a2qyeprif"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-0815ab40a03037e73c5c91e2688b22f1",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "69"
          }, {
            "name" : "role_jceks_password",
            "value" : "227nmmc1xwg1otl5f7htfpxc0"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-e79b3b03c47cf9209a0a43cbd23f8719",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "63"
          }, {
            "name" : "role_jceks_password",
            "value" : "9nui86s7kphs5bubvwr6crhw6"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406",
    "ipAddress" : "10.0.0.4",
    "hostname" : "gianbo01",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "6dfa6b11-9a45-4171-8fd4-b2b8ff9d355b",
    "ipAddress" : "10.0.0.5",
    "hostname" : "gianbo02",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "6010efad-fa18-4e11-ae3f-b9c75567e29d",
    "ipAddress" : "10.0.0.6",
    "hostname" : "gianbo03",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "f0718492-da6c-458d-b578-8e27c1a2f43b",
    "ipAddress" : "10.0.0.7",
    "hostname" : "gianbo04",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "328f89a6-bbe4-4e6e-b8d7-08d2747254f6",
    "ipAddress" : "10.0.0.8",
    "hostname" : "gianbo05",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__1c0ea9fe-f528-40df-aa9a-7865943e08e3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "612b119c280af5aa2a0ee1eb9eaacb6e74d9a8defdd189ed3f6d2a05aba51873",
    "pwSalt" : -4241468162463866668,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__afeb9773-fbd5-4b45-a5bc-e4333af6edb3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "91e6477835f80f5012dfc5cd17c57bd3003f84b9991ca8757db511ddebe41cdf",
    "pwSalt" : 101936881089952725,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__bd90e7a2-a52c-4b07-a76a-67ff528126ce",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "f846f3b194a64de5b815d5b17c61ec9cb048557f76a9c135dae5f0dc28600005",
    "pwSalt" : -289019805482947205,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__hue-HUE_SERVER-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_NAVIGATOR_ADMIN" ],
    "pwHash" : "81efca7e47a21e8250d5923cf2cdb493b917d41b25e80e12f577ed0a6e8ef219",
    "pwSalt" : -7864219814557953362,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "43774033b9dc85d0550ce5e5b011ec0acce51048351a470b4ec1b2e6be45ee1d",
    "pwSalt" : 5706459862795550604,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "72df29798916dabeec3780f5bb3ac97bbda85387999bbf638bf8e8abaaba84c5",
    "pwSalt" : -4190198015912449703,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "09ca60acda4d83bc77ab712ddfb88e17f327f1e96ec27efd9ef69fc9c6ffaf13",
    "pwSalt" : 3890688487973978142,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "c1e9eb4e14fa95c1e3decf5136e127350c9980e89562e948733c62199c3996aa",
    "pwSalt" : 6225347986457263883,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "e3676c5f68b3b6b101e98a572baefd76539cfc054a9b621d86b5071c3b6117a7",
    "pwSalt" : 6261632021201754158,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "c2f16a9f5d9276ac801b47e54d233affa73834a14a9ea31e430ec29a4fc4beb3",
    "pwSalt" : -9080618991741372173,
    "pwLogin" : true
  }, {
    "name" : "gianfolo",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "36683fb4cbc02a193f770adbf5e401b70a42d4c7769a530ab229724da06d5cbd",
    "pwSalt" : 2067303969607290672,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "fba82743d0a5d8763dffc316cb4f6e34ff8114de25e614dcb9278ac97f294400",
    "pwSalt" : 1719358482903258609,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.13.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20180328-1830",
    "gitHash" : "f90c58536c252d70a23bde6d94514d92a1f111d4",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "gianbo01"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "ABCD1_amon"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        }, {
          "name" : "firehose_heapsize",
          "value" : "602931200"
        } ]
      }, {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "602931200"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "602931200"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "gianbo01"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "ABCD1_rman"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "602931200"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "602931200"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "1p8pb1187j1r0gu0680e0gb5s"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "918cq0ihh6yiiwzl29qp5w0ef"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "dyaxznc80g5m7skuc0nqw0ecs"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "9tes5gxeydn1q9lssoav731bx"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "anfd59x0bnq5tzj3jb7q5krgz"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-e79b3b03c47cf9209a0a43cbd23f8719",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "b0e67fc8-1b13-4938-8936-f400105bd406"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "juk2wrrsl80qru5a1kqslgaa"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/26/2012 14:50"
    }, {
      "name" : "PARCEL_UPDATE_FREQ",
      "value" : "1"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "NOT_ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://gianbo05/cloudera-repos/cdh5/parcels/5.13.3"
    } ]
  }
}
```
