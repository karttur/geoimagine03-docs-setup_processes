---
layout: article
title: CopernicusProcess_root+search+download_v090.json
categories: setup_processes
excerpt:  Install processes for searching, downloading and organising Copernicus data
tags:: 
    - json/CopernicusProcess_root+search+download
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/CopernicusProcess root+search+download (setup_processes)

###  Install processes for searching, downloading and organising Copernicus data

The json command file <span class='file'>CopernicusProcess_root+search+download_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "CopernicusProc",
        "title": "Manage Copernicus processes",
        "label": "Specific Copernicus processes (order, download, organize)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "CopernicusProc",
        "subprocid": "SearchCopernicusProducts",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Access available files in Copernicus holding",
        "label": "Requires setup of wget and Copernicus credentials file (called .netrc in user home path)"
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
              "defaultvalue": "",
              "hint": "Copernicus product to search"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "product version to search"
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "gisco-services.ec.europa.eu",
              "hint": "Serverurl for Copernicus data"
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
        "rootprocid": "CopernicusProc",
        "subprocid": "DownloadCopernicus",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Download Copernicus data",
        "label": "Download Copernicus data"
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
              "defaultvalue": "",
              "hint": "Copernicus product to download"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Copernicus product version to download",
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
              "hint": "Source volume with Copernicus data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "Copernicus raw data file type header"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "Copernicus raw data file type data"
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
        "subprocid": "UnZipRawData",
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
              "paramid": "getlist",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "csvfile-getpath1",
              "hint": "Alternatives for getting the files to unzip"
            },
            {
              "paramid": "pattern",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "pattern to search in zip file"
            },
            {
              "paramid": "patternreplace",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "pattern",
              "hint": "Replace string for search pattern"
            },
            {
              "paramid": "zipreplace",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ".tif",
              "hint": "extention replace string"
            },
            {
              "paramid": "path",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Path to json object listing urls"
            },
            {
              "paramid": "rootdir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Dst datadir for downloads"
            },
            {
              "paramid": "srcsubdir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Subdir with zip files"
            },
            {
              "paramid": "dstsubdir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Subdirfor exploded layers"
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
        "subprocid": "BBoxTiledRawData",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Bounding box for raw tiles",
        "label": "Bounding box for raw tiles"
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
              "paramid": "getlist",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "csvfile-getpath1",
              "hint": "Alternatives for getting the files to unzip"
            },
            {
              "paramid": "pattern",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "pattern to search in filelist"
            },
            {
              "paramid": "srcpath",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Path to folder holding raw data tiles"
            },
            {
              "paramid": "dstpath",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Path to vector file"
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
