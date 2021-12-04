---
layout: article
title: db-dump-all_v090.json
categories: setup_processes
excerpt:  Dump all databases (definitions, data and complete in three separate files)
tags:: 
    - json/db-dump-all
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/db dump all (setup_processes)

###  Dump all databases (definitions, data and complete in three separate files)

The json command file <span class='file'>db-dump-all_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "processid": "ExportDatabaseCsv",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "p",
        "cmdpath": "/usr/local/bin",
        "dataonly": false,
        "definitiononly": true
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "p",
        "cmdpath": "/usr/local/bin",
        "dataonly": true,
        "definitiononly": false
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "p",
        "cmdpath": "/usr/local/bin",
        "dataonly": false,
        "definitiononly": false
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "c",
        "cmdpath": "/usr/local/bin",
        "dataonly": false,
        "definitiononly": true
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "c",
        "cmdpath": "/usr/local/bin",
        "dataonly": true,
        "definitiononly": false
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    },
    {
      "processid": "DumpDatabaseSQL",
      "overwrite": true,
      "version": "0.9",
      "verbose": 2,
      "parameters": {
        "format": "c",
        "cmdpath": "/usr/local/bin",
        "dataonly": false,
        "definitiononly": false
      },
      "dstpath": {
        "volume": ".",
        "hdr": "shp",
        "dat": "shp"
      }
    }
  ]
}
```
