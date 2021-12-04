---
layout: article
title: db-restore-all_v090.json
categories: setup_processes
excerpt:  Restore (as sql) and import (csv) all Framework database schemas and tables
tags:: 
    - json/db-restore-all
date: 2021-12-04
modified: 2021-12-04
comments: true
share: true
---

# json/db restore all (setup_processes)

###  Restore (as sql) and import (csv) all Framework database schemas and tables

The json command file <span class='file'>db-restore-all_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

```
{
  "userproject": {
    "userid": "karttur",
    "projectid": "karttur",
    "tractid": "karttur",
    "siteid": "*",
    "plotid": "*",
    "system": "system"
  },
  "period": {
    "timestep": "static"
  },
  "process": [
    {
      "processid": "RestoreDatabaseSQL",
      "overwrite": false,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "p",
        "cmdpath": "/usr/local/bin",
        "dataonly": true,
        "definitiononly": true
      },
      "srcpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "InsertDatabaseCsv",
      "overwrite": false,
      "version": "0.9",
      "verbose": 2,
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      },
      "srcpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    }
  ]
}
```
