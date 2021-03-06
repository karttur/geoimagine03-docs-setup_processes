---
layout: article
title: modisProcess_root+search+download_v090.json
categories: setup_processes
excerpt:  Install MODIS root process and the subprocesses for searching and downloading MODIS tiles
tags:: 
    - json/modisProcess_root+search+download
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/modisProcess root+search+download (setup_processes)

###  Install MODIS root process and the subprocesses for searching and downloading MODIS tiles

The json command file <span class='file'>modisProcess_root+search+download_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "MODISProc",
        "title": "Manage MODIS processes",
        "label": "Specific MODIS processes (order, download, organize)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "MODISProc",
        "subprocid": "SearchModisProducts",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Access available files in Data pool holding",
        "label": "Requires setup of wget and EarthData credentials file (called .netrc in user home path)"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
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
              "hint": "MODIS product to search",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "product version to search",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
                }
              ]
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "https://e4ftl01.cr.usgs.gov",
              "hint": "Serverurl for MODIS data",
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
        "rootprocid": "MODISProc",
        "subprocid": "ModisSearchToDB",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Transfer the MODIS seanch results to the postgres DB",
        "label": "Open and reads html formatted files from searchDataPool"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "none",
          "dstdivision": "none",
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
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MCD43A4",
              "hint": "MODIS product to load",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "MODIS product version to load",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
                }
              ]
            },
            {
              "paramid": "searchdone",
              "paramtyp": "Boolean",
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
              "defaultvalue": "",
              "hint": "source path"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "MODISProc",
        "subprocid": "DownloadDataPool",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download MODIS tile data from MODIS datapool",
        "label": "Download MODIS tile data from MODIS datapool"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
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
              "hint": "MODIS product to download",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "MODIS product version to download",
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
              "hint": "Source volume with MODIS data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "MODIS raw data file type header"
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
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "MODISProc",
        "subprocid": "DownloadModisSingleTile",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download MODIS tile data from MODIS datapool",
        "label": "Download MODIS tile data from MODIS datapool"
      },
      "system": [
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
              "paramid": "remoteuser",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": "",
              "hint": "Remote user on server with MODIS data"
            },
            {
              "paramid": "serverurl",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "https://e4ftl01.cr.usgs.gov",
              "hint": "Remote server with MODIS data"
            },
            {
              "paramid": "asscript",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "True",
              "hint": "Output as script of direct download"
            },
            {
              "paramid": "searchdone",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False",
              "hint": "Search for already downloaded"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MCD43A4",
              "hint": "MODIS product to download",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "MODIS product version to download",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
                }
              ]
            },
            {
              "paramid": "xtile",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "MODIS xtile to download"
            },
            {
              "paramid": "ytile",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "MODIS ytile to download"
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
              "hint": "Destination volume"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "MODISProc",
        "subprocid": "DownloadModisRegionTiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download MODIS tile data from MODIS datapool",
        "label": "Download MODIS tile data from MODIS datapool"
      },
      "system": [
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
              "paramid": "remoteuser",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": "",
              "hint": "Remote user on server with MODIS data"
            },
            {
              "paramid": "serverurl",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "https://e4ftl01.cr.usgs.gov",
              "hint": "Remote server with MODIS data"
            },
            {
              "paramid": "asscript",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "True",
              "hint": "Output as script of direct download"
            },
            {
              "paramid": "searchdone",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False",
              "hint": "Search for already downloaded"
            },
            {
              "paramid": "temporaldisplacement",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0",
              "hint": "The relative doy to search for particular date"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MCD43A4",
              "hint": "MODIS product to download",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "MODIS product version to download",
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
              "hint": "Destination volume for download"
            }
          ]
        }
      ]
    }
  ]
}
```
