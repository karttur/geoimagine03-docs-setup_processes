---
layout: article
title: timeseriesprocesses_image-mend_v090.json
categories: setup_processes
excerpt:  Install processes for filling gaps in time series data
tags:: 
    - json/timeseriesprocesses_image-mend
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/timeseriesprocesses image mend (setup_processes)

###  Install processes for filling gaps in time series data

The json command file <span class='file'>timeseriesprocesses_image-mend_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "subprocid": "TimeSeriesImageMend",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Mend image timeseries data"
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
          "parameter": [
            {
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1to1"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "method",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "interpolate"
            },
            {
              "paramid": "validfraction",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0.5
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
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
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
          "parent": "dstcomp",
          "element": "*",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "src"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "src"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "src"
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
              "defaultvalue": "*"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*"
            }
          ]
        }
      ]
    }
  ]
}
```
