---
layout: article
title: regions_custom-define_v090.json
categories: setup_processes
excerpt:  Install process for defining custom region
tags:: 
    - json/regions_custom-define
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions custom define (setup_processes)

###  Install process for defining custom region

The json command file <span class='file'>regions_custom-define_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

```
{
  "postgresdb": {
    "db": "geoimagine"
  },
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
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "DefineCustomSystem",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Define a custom system",
        "label": "Define a custom Frameworksystem"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
          "srcdivision": "region",
          "dstdivision": "none",
          "srcepsg": 0,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "systemid",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": "slick",
              "hint": "System identifier for the new system to be creaed"
            },
            {
              "paramid": "epsg",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "0",
              "hint": "The epsg code for the custom projection syste,"
            },
            {
              "paramid": "minx",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "maxx",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "miny",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "maxy",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "xtiles",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "ytiles",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "0"
            },
            {
              "paramid": "removenoneearthttiles",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            }
          ]
        }
      ]
    }
  ]
}
```
