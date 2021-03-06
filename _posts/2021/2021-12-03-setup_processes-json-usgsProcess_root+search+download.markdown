---
layout: article
title: usgsProcess_root+search+download_v090.json
categories: setup_processes
excerpt:  Install processes for searching, downloading and organising USGS data
tags:: 
    - json/usgsProcess_root+search+download
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/usgsProcess root+search+download (setup_processes)

###  Install processes for searching, downloading and organising USGS data

The json command file <span class='file'>usgsProcess_root+search+download_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "USGSProc",
        "title": "Manage USGS processes",
        "label": "Specific USGS processes (order, download, organize)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "USGSProc",
        "subprocid": "SearchUSGSProducts",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Access available files in Data pool holding",
        "label": "Requires setup of wget and EarthData credentials file (called .netrc in user home path)"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MCD43A4",
              "hint": "USGS product to search"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "product version to search"
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "https://e4ftl01.cr.usgs.gov",
              "hint": "Serverurl for USGS data",
              "setvalue": [
                {
                  "value": "https://e4ftl01.cr.usgs.gov",
                  "label": "https://e4ftl01.cr.usgs.gov"
                }
              ]
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
        "rootprocid": "USGSProc",
        "subprocid": "DownloadUSGS",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Download USGS data",
        "label": "Download USGS data"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "remoteuser",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "user",
              "hint": "Server user"
            },
            {
              "paramid": "password",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "password",
              "hint": "Server password"
            },
            {
              "paramid": "searchdone",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": false,
              "hint": "Re-saerch products"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MCD43A4",
              "hint": "USGS product to download"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "USGS product version to download",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
                }
              ]
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
              "defaultvalue": "",
              "hint": "Source volume with USGS data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "USGS raw data file type header"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "MODIS raw data file type data"
            }
          ]
        }
      ]
    }
  ]
}
```
