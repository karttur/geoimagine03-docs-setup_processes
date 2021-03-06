---
layout: article
title: periodicity_v090.json
categories: setup_processes
excerpt:  Install periodicity processing used in all scripts handling actual spatial data
tags:: 
    - json/periodicity
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/periodicity (setup_processes)

###  Install periodicity processing used in all scripts handling actual spatial data

The json command file <span class='file'>periodicity_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

```
{
  "process": [
    {
      "processid": "addrootproc",
      "parameters": {
        "rootprocid": "Periodicity",
        "title": "Period settings",
        "label": "Processes for setting periods of all spatial data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Periodicity",
        "subprocid": "Periodicity",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Period settings",
        "label": "Processes for setting periods of all spatial data"
      },
      "system": [
        {
          "system": "*",
          "srcsystem": "NA",
          "dstsystem": "NA",
          "srcdivision": "NA",
          "dstdivision": "NA",
          "srcepsg": 0,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "period",
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
              "paramid": "seasonalts",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Is this a seasonal signal"
            },
            {
              "paramid": "averagets",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Is this a seasonal signal"
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
                },
                {
                  "value": "V",
                  "label": "Varying timestep (typically for optical satellite images)"
                },
                {
                  "value": "M",
                  "label": "Monthly timestep (typically for climate data)."
                },
                {
                  "value": "A",
                  "label": "Annual data"
                },
                {
                  "value": "8D",
                  "label": "Every 8th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "16D",
                  "label": "Every 16th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "32D",
                  "label": "Every 32nd day timeseries (originating from MODIS defualt products)"
                }
              ]
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcperiod",
          "parameter": [
            {
              "paramid": "addons",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0",
              "hint": "Addons for source time series that differes from process timeseries",
              "minmax": {
                "min": "0",
                "max": "12"
              }
            },
            {
              "paramid": "maxdaysaddons",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0",
              "hint": "Type of time series (loosely based on Pandas)",
              "minmax": {
                "min": "0",
                "max": "120"
              }
            },
            {
              "paramid": "timestep",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "NA",
              "hint": "Type of time series (loosely based on Pandas)",
              "setvalue": [
                {
                  "value": "NA",
                  "label": "Not Applicable (use main process time step setting)"
                },
                {
                  "value": "S",
                  "label": "Static (no timestep)"
                },
                {
                  "value": "V",
                  "label": "Varying timestep (typically for optical satellite images)"
                },
                {
                  "value": "M",
                  "label": "Monthly timestep (typically for climate data)."
                },
                {
                  "value": "A",
                  "label": "Annual data"
                },
                {
                  "value": "8D",
                  "label": "Every 8th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "16D",
                  "label": "Every 16th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "32D",
                  "label": "Every 32nd day timeseries (originating from MODIS defualt products)"
                }
              ]
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstperiod",
          "parameter": [
            {
              "paramid": "timestep",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "NA",
              "hint":"Destination data set timestep if different from process timestep",
              "setvalue": [
                {
                  "value": "NA",
                  "label": "Not Applicable (use main process time step setting)"
                },
                {
                  "value": "S",
                  "label": "Static (no timestep)"
                },
                {
                  "value": "V",
                  "label": "Varying timestep (typically for optical satellite images)"
                },
                {
                  "value": "M",
                  "label": "Monthly timestep (typically for climate data)."
                },
                {
                  "value": "A",
                  "label": "Annual data"
                },
                {
                  "value": "8D",
                  "label": "Every 8th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "16D",
                  "label": "Every 16th day timeseries (originating from MODIS defualt products)"
                },
                {
                  "value": "32D",
                  "label": "Every 32nd day timeseries (originating from MODIS defualt products)"
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```
