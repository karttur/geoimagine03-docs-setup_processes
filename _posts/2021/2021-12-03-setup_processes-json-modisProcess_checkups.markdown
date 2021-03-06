---
layout: article
title: modisProcess_checkups_v090.json
categories: setup_processes
excerpt:  Install MODIS processes for checking and updating the db and the local disk catalogue of MODIS data
tags:: 
    - json/modisProcess_checkups
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/modisProcess checkups (setup_processes)

###  Install MODIS processes for checking and updating the db and the local disk catalogue of MODIS data

The json command file <span class='file'>modisProcess_checkups_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "MODISProc",
        "subprocid": "CheckModisBands",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Check MODIS organization",
        "label": "Checks MODIS downloads and files on local system compared to db"
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
              "paramid": "organized",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "Organized or not?"
            },
            {
              "paramid": "redundant",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "Redundant or not?"
            },
            {
              "paramid": "download",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "Downloaded or not?"
            },
            {
              "paramid": "extract",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "Extracted or not?"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcperiod",
          "parameter": [
            {
              "paramid": "timestep",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "allscenes",
              "hint": "Timestep code (default = allscenes)"
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
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tif",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "to be completed"
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
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tif",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "to be completed"
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
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "original",
              "hint": "to be completed"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "to be completed"
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
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "SRFI",
              "hint": "to be completed"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "to be completed"
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
        "subprocid": "CheckModisScenes",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Check MODIS organization",
        "label": "Checks MODIS downloads and files on local system compared to db"
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
              "paramid": "redundant",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "to be completed"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcperiod",
          "parameter": [
            {
              "paramid": "timestep",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "allscenes"
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
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "to be completed"
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
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "original",
              "hint": "to be completed"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "N",
              "hint": "to be completed"
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
        "subprocid": "CheckModisSingleTile",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Extracts the content of modis scenes>",
        "label": "Scenes must be organized prior to extration"
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
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
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
              "defaultvalue": "",
              "hint": "to be completed",
              "setvalue": [
                {
                  "value": "005",
                  "label": "version 005"
                },
                {
                  "value": "006",
                  "label": "version 006"
                }
              ]
            },
            {
              "paramid": "checkdownloaded",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True",
              "hint": "to be completed"
            },
            {
              "paramid": "checkexploded",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True",
              "hint": "to be completed"
            },
            {
              "paramid": "xtile",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "to be completed"
            },
            {
              "paramid": "ytile",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "to be completed"
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
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "to be completed"
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
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tif",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "to be completed"
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
        "subprocid": "CheckModisRegion",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Extracts the content of modis scenes>",
        "label": "Scenes must be organized prior to extration"
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
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
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
              "defaultvalue": "",
              "setvalue": [
                {
                  "value": "005",
                  "label": "version 005"
                },
                {
                  "value": "006",
                  "label": "version 006"
                }
              ]
            },
            {
              "paramid": "checkdownloaded",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "checkexploded",
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
              "required": false,
              "defaultvalue": "hdf"
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
              "required": false,
              "defaultvalue": "tif"
            },
            {
              "paramid": "dat",
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
