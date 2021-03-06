---
layout: article
title: updateLayer_v090.json
categories: setup_processes
excerpt:  Install processes for updating the database
tags:: 
    - json/updateLayer
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/updateLayer (setup_processes)

###  Install processes for updating the database

The json command file <span class='file'>updateLayer_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "UpdateDb",
        "title": "Update Database",
        "label": "Update Database"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "UpdateDb",
        "subprocid": "UpdateDbRegion",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Update",
        "label": "Update"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "dummy",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "dummy"
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
              "hint": "Volume, disk or path for saving the destination data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "Header or header+data file extension (default = shp)"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Data file extension for datasets with separate header + data file"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "layer",
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
              "required": false,
              "defaultvalue": "",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "N",
              "hint": "Destination data scale measure",
              "setvalue": [
                {
                  "value": "N",
                  "label": "nominal"
                },
                {
                  "value": "O",
                  "label": "ordinal"
                },
                {
                  "value": "I",
                  "label": "interval"
                },
                {
                  "value": "R",
                  "label": "ratio"
                }
              ]
            },
            {
              "paramid": "masked",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Whether the data is masked or not"
            },
            {
              "paramid": "cellnull",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)",
              "setvalue": [
                {
                  "value": "Byte",
                  "label": "Unisgned 8 bit"
                }
              ]
            },
            {
              "paramid": "scalefac",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 1,
              "hint": "Scale factor for raster data (default = 1.0, no scaling)"
            },
            {
              "paramid": "offsetadd",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0,
              "hint": "Offset add default = 0, no adding"
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Data unit for raster cell data"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "UpdateDb",
        "subprocid": "UpdateDbTiles",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Update",
        "label": "Update"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
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
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "dummy",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "dummy"
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
              "hint": "Volume, disk or path for saving the destination data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "Header or header+data file extension (default = shp)"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Data file extension for datasets with separate header + data file"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "layer",
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
              "required": false,
              "defaultvalue": "",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "N",
              "hint": "Destination data scale measure",
              "setvalue": [
                {
                  "value": "N",
                  "label": "nominal"
                },
                {
                  "value": "O",
                  "label": "ordinal"
                },
                {
                  "value": "I",
                  "label": "interval"
                },
                {
                  "value": "R",
                  "label": "ratio"
                }
              ]
            },
            {
              "paramid": "masked",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Whether the data is masked or not"
            },
            {
              "paramid": "cellnull",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)",
              "setvalue": [
                {
                  "value": "Byte",
                  "label": "Unisgned 8 bit"
                }
              ]
            },
            {
              "paramid": "scalefac",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "1",
              "hint": "Scale factor for raster data (default = 1.0, no scaling)"
            },
            {
              "paramid": "offsetadd",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0",
              "hint": "Offset add default = 0, no adding"
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Data unit for raster cell data"
            }
          ]
        }
      ]
    }
  ]
}
```
