---
layout: article
title: timeseriesprocesses_indexcrosstrend_v090.json
categories: setup_processes
excerpt:  Install process for index time series cross trend analysis
tags:: 
    - timeseriesprocesses_indexcrosstrend
date: 2021-11-08
modified: 2021-11-08
comments: true
share: true
---

# timeseriesprocesses indexcrosstrend (setup_processes)

###  Install process for index time series cross trend analysis

The json command file <span class='file'>timeseriesprocesses_indexcrosstrend_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
  "process": [
    {
      "processid": "addsubproc",
      "overwrite": true,
      "parameters": {
        "rootprocid": "TimeSeries",
        "subprocid": "TimeSeriesIndexCrossTrend",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Index time-series cross trends"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "required": true,
          "parameter": [
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "indexcrosstrend"
            },
            {
              "paramid": "mirrorlag",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "maxlag",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "6"
            },
            {
              "paramid": "savelags",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "-1"
            },
            {
              "paramid": "normalize",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "standardize",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "naive",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "False",
              "alt": {
                "True": "naive",
                "False": "seasonal"
              }
            },
            {
              "paramid": "additive",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "True",
              "alt": {
                "True": "additive",
                "False": "multiplicative"
              }
            },
            {
              "paramid": "yearfac",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "1"
            },
            {
              "paramid": "trend",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "spline"
            },
            {
              "paramid": "prefilterseason",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "kernel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "forceseason",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "abs",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "xcrossobserved",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "xcrosstendency",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "xcrosseason",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "xcrossresidual",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "xcrosspearson",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "xcrosslag",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcpath",
          "parameter": [
            {
              "paramid": "volume",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "tif"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstpath",
          "parameter": [
            {
              "paramid": "volume",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "tif"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            }
          ]
        },
        {
          "parent": "process",
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "*",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "parent",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "process"
            },
            {
              "paramid": "element",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            }
          ]
        },
        {
          "parent": "srccomp",
          "element": "*",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            }
          ]
        },
        {
          "parent": "process",
          "element": "index",
          "parameter": [{
            "paramid": "id",
            "paramtyp": "text",
            "required": true,
            "defaultvalue": ""
          }
        ]
        },
        {
          "parent": "process",
          "element": "stats",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            }
          ]
        }
      ]
    }
  ]
}
```
