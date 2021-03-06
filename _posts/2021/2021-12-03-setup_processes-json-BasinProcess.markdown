---
layout: article
title: BasinProcess_v090.json
categories: setup_processes
excerpt:  Install processes for retrieving hydrological basins from DEM
tags:: 
    - json/BasinProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/BasinProcess (setup_processes)

###  Install processes for retrieving hydrological basins from DEM

The json command file <span class='file'>BasinProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "BasinProc",
        "title": "basin processes",
        "label": "River basin processes)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "BasinProc",
        "subprocid": "BasinOutletTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Refine pre-identified basin mouths in tiles data",
        "label": "Refine pre-identified basin mouths and adjust DEM to a signle outlet point in tiled data"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "ease2n",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "ease2s",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6932,
          "dstepsg": 6932
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "ease2t",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6933,
          "dstepsg": 6933
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "tiltmouths",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Tilt DEM at moouth to single outlet"
            },
            {
              "paramid": "grassdem",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "DEM",
              "hint": "Name of GRASS internal DEM file (default: DEM)"
            },
            {
              "paramid": "outlet",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "MOUTH",
              "hint": "MOUTH, SFD or MFD"
            },
            {
              "paramid": "distill",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "MOUTH",
              "hint": "MFD, MOUTH or None"
            },
            {
              "paramid": "clusteroutlet",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "maximum",
              "hint": "methods for finding single outlet point"
            },
            {
              "paramid": "basincelltrehshold",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": -1,
              "hint": "minimum nr of cells to form a basin"
            },
            {
              "paramid": "watershed",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "MFD",
              "hint": "MFD [nr] or SFD"
            },
            {
              "paramid": "memory",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300,
              "hint": "memory assignment in MB"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true,
              "hint": "whether to run as script or inside python"
            },
            {
              "paramid": "mosaic",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true,
              "hint": "whether to use mosaicked tiles or not"
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
        },
        {
          "parent": "process",
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "*",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "*",
              "hint": "link for source composition"
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
              "defaultvalue": "",
              "hint": "Source instrument, method, model or similar of import layer (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Import layer product, producer or similary (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Import layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*",
              "hint": "Import layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Import layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Import layer syffix (usually identical to id)"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcopy",
          "parameter": [
            {
              "paramid": "srccomp",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*",
              "hint": "unknown hint"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            }
          ]
        }
      ]
    }
  ]
}
```
