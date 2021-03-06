---
layout: article
title: timeseriesprocesses_root-resample_v090.json
categories: setup_processes
excerpt:  Install time series processing root and resample
tags:: 
    - json/timeseriesprocesses_root-resample
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/timeseriesprocesses root resample (setup_processes)

###  Install time series processing root and resample

The json command file <span class='file'>timeseriesprocesses_root-resample_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "processid": "addrootproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "TimeSeries",
        "title": "Timeseries analysis",
        "label": "Timeseries analysis"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "TimeSeries",
        "subprocid": "TimeSeriesResmple",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Resample time series to other interval"
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
              "paramid": "group",
              "paramtyp": "bool",
              "required": true,
              "defaultvalue": false
            },
            {
              "paramid": "method",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "avg"
            }
          ]
        },
        {
          "parent": "process",
          "element": "tarperiod",
          "parameter": [
            {
              "paramid": "startyear",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1900,
              "hint": "year of first data point"
            },
            {
              "paramid": "endyear",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2100,
              "hint": "year of last data point"
            },
            {
              "paramid": "startmonth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1,
              "hint": "month of first data point",
              "minmax": {
                "min": 1,
                "max": 12
              }
            },
            {
              "paramid": "endmonth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12,
              "hint": "month of last data point",
              "minmax": {
                "min": 1,
                "max": 12
              }
            },
            {
              "paramid": "startday",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1,
              "hint": "day of month of first data point",
              "minmax": {
                "min": 1,
                "max": 31
              }
            },
            {
              "paramid": "endday",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 31,
              "hint": "day of month of last data point",
              "minmax": {
                "min": 1,
                "max": 31
              }
            },
            {
              "paramid": "seasonstartmonth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1,
              "hint": "first month of seasonal data",
              "minmax": {
                "min": 1,
                "max": 12
              }
            },
            {
              "paramid": "seasonendmonth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12,
              "hint": "last month of seasonal data",
              "minmax": {
                "min": 1,
                "max": 12
              }
            },
            {
              "paramid": "seasonstartday",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1,
              "hint": "First day of month of seasonal data",
              "minmax": {
                "min": 1,
                "max": 31
              }
            },
            {
              "paramid": "seasonendday",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 31,
              "hint": "Last day of month of seasonal data",
              "minmax": {
                "min": 1,
                "max": 31
              }
            },
            {
              "paramid": "addons",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0,
              "hint": "added timesteps at start and end"
            },
            {
              "paramid": "maxdaysaddons",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0,
              "hint": "Maximum number of days allowed for adding to start and end"
            },
            {
              "paramid": "timestep",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "static",
              "hint": "Type of time series (loosely based on Pandas)",
              "setvalue": [
                {
                  "value": "S",
                  "label": "Static (no timestep)"
                }
              ]
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
              "defaultvalue": "src"
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
              "defaultvalue": false
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstlayer",
          "parameter": [
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
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
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "scalefac",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "offsetadd",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            }
          ]
        }
      ]
    }
  ]
}
```
