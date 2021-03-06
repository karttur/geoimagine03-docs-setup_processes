---
layout: article
title: grassProcess_v090.json
categories: setup_processes
excerpt:  Install processes for bundling to GRASS GIS
tags:: 
    - json/grassProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/grassProcess (setup_processes)

###  Install processes for bundling to GRASS GIS

The json command file <span class='file'>grassProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "parameters": {
        "rootprocid": "GrassProc",
        "title": "Grass GIS processes binding",
        "label": "Bindings for any GRASS GIS processing"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "GrassProc",
        "subprocid": "Grass1to1Tiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Grass binding for tile processes 1 to 1",
        "label": "Uses the grass-session script for binding processes with one input and one output."
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
              "paramid": "mosaic",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "regionlayer",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Layer that defined the default region of the location"
            },
            {
              "paramid": "subparameter",
              "paramtyp": "list",
              "required": true,
              "defaultvalue": ""
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
            },
            {
              "paramid": "cellnull",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
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
              "paramid": "masked",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Whether the data is masked or not"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "GrassProc",
        "subprocid": "GrassOnetoManyTiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Grass binding for tile processes 1 to many",
        "label": "Uses the grass-session script for binding processes with one input and multiple outputs."
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
              "paramid": "mosaic",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "regionlayer",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Layer that defined the default region of the location"
            },
            {
              "paramid": "subparameter",
              "paramtyp": "list",
              "required": true,
              "defaultvalue": ""
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
            },
            {
              "paramid": "cellnull",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto",
              "hint": "unknown hint"
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
              "paramid": "masked",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Whether the data is masked or not"
            }
          ]
        }
      ]
    }
  ]
}
```
