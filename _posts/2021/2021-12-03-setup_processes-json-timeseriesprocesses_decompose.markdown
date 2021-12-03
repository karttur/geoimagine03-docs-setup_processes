---
layout: article
title: timeseriesprocesses_decompose_v090.json
categories: setup_processes
excerpt:  Install processes for time series decompositon
tags:: 
    - json/timeseriesprocesses_decompose
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/timeseriesprocesses decompose (setup_processes)

###  Install processes for time series decompositon

The json command file <span class='file'>timeseriesprocesses_decompose_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "overwrite": false,
      "parameters": {
        "rootprocid": "TimeSeries",
        "subprocid": "TimeSeriesDecompose",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Time-series decomposition"
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
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "decomposets"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
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
              "defaultvalue": "decomp"
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
        }
      ]
    }
  ]
}
```
