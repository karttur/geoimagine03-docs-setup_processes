---
layout: article
title: ancillary_tandemX-download_v090.json
categories: setup_processes
excerpt:  Install download processes for Tandem X data
tags:: 
    - json/ancillary_tandemX-download
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/ancillary tandemX download (setup_processes)

###  Install download processes for Tandem X data

The json command file <span class='file'>ancillary_tandemX-download_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "Ancillary",
        "title": "Ancillary data processing",
        "label": "Processes for downloading and organizing ancillary data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Ancillary",
        "subprocid": "SearchJsonTandemX",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Search local geojson file for tiles to download",
        "label": "Search local geojson file for TanDEM-X tiles to download"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "NA",
          "dstdivision": "NA",
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
              "paramid": "path",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Path to json object listing urls"
            },
            {
              "paramid": "datadir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Dst datadir for downloads"
            },
            {
              "paramid": "username",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "username",
              "hint": "Users"
            },
            {
              "paramid": "password",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "password",
              "hint": "Password"
            },
            {
              "paramid": "minlon",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": -180,
              "hint": "Minimum longitude"
            },
            {
              "paramid": "minlat",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": -90,
              "hint": "Minimum latitude"
            },
            {
              "paramid": "maxlon",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 180,
              "hint": "Maximum longitude"
            },
            {
              "paramid": "maxlat",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 90,
              "hint": "Maximum latitude"
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
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Ancillary",
        "subprocid": "UnZipTandemX",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Search local geojson file for tiles to unzip",
        "label": "Search local geojson file for TanDEM-X tiles to unzip"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "NA",
          "dstdivision": "NA",
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
              "paramid": "path",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Path to json object listing urls"
            },
            {
              "paramid": "datadir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Dst datadir for downloads"
            },
            {
              "paramid": "minlon",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": -180,
              "hint": "Minimum longitude"
            },
            {
              "paramid": "minlat",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": -90,
              "hint": "Minimum latitude"
            },
            {
              "paramid": "maxlon",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 180,
              "hint": "Maximum longitude"
            },
            {
              "paramid": "maxlat",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 90,
              "hint": "Maximum latitude"
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
            }
          ]
        }
      ]
    }
  ]
}
```
