---
layout: article
title: timeseriesprocesses_imagecrosstrend_v090.json
categories: setup_processes
excerpt:  Install process for image time series cross trend analysis
tags:: 
    - timeseriesprocesses_imagecrosstrend
date: 2021-11-08
modified: 2021-11-08
comments: true
share: true
---

# timeseriesprocesses imagecrosstrend (setup_processes)

###  Install process for image time series cross trend analysis

The json command file <span class='file'>timeseriesprocesses_imagecrosstrend_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "subprocid": "TimeSeriesImageCrossTrend",
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
              "required": false,
              "defaultvalue": "imagecrosstrend"
            },
            {
              "paramid": "mirrorlag",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
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
              "paramid": "master",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": ""
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
              "defaultvalue": "master"
            }
          ]
        },
        {
          "parent": "srccomp",
          "element": "master",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "master"
            },
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
              "defaultvalue": "master"
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
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "slave",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": ""
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
              "defaultvalue": "slave"
            }
          ]
        },
        {
          "parent": "srccomp",
          "element": "slave",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "slave"
            },
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
              "defaultvalue": "slave"
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
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "*",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": ""
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
          "parent": "dstcomp",
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
              "required": false,
              "defaultvalue": "xcorr"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "noeffect"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "auto"
            }
          ]
        }
      ]
    }
  ]
}
```
