---
layout: article
title: timeseriesprocesses_correlate-lags_v090.json
categories: setup_processes
excerpt:  Install processes for correlating lag times
tags:: 
    - json/timeseriesprocesses_correlate-lags
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/timeseriesprocesses correlate lags (setup_processes)

###  Install processes for correlating lag times

The json command file <span class='file'>timeseriesprocesses_correlate-lags_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "subprocid": "TimeSeriesCorrelateLag",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Time-series correlation for lag"
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
        },
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
              "paramid": "spatialforce",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
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
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
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
              "defaultvalue": "auto"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "dst"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "Y"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcforce",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
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
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
            }
          ]
        }
      ]
    }
  ]
}
```
