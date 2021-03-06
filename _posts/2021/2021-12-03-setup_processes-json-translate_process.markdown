---
layout: article
title: translate_process_v090.json
categories: setup_processes
excerpt:  Install processes binding to GDAL translate
tags:: 
    - json/translate_process
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/translate process (setup_processes)

###  Install processes binding to GDAL translate

The json command file <span class='file'>translate_process_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "Translate",
        "title": "Translate data",
        "label": "Translate data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Translate",
        "subprocid": "TranslateRegion",
        "version": "0.9.0",
        "minuserstratum": 5,
        "title": "Translate regional data"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6842,
          "dstepsg": 6842
        },
        {
          "system": "landsat",
          "srcsystem": "landsat",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 3200,
          "dstepsg": 3200
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "ease2s",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6932,
          "dstepsg": 6932
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "ease2t",
          "srcdivision": "region",
          "dstdivision": "rgeion",
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
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "dstEPSG",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "xoff",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "yoff",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "xsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "ysize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "tr_xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "tr_yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "resample",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "near"
            },
            {
              "paramid": "autofitextent",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "src_min",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "src_max",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_min",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_max",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "exponent",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "unscale",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "dst_ulx",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_uly",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_lrx",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_lry",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "nodata",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "-22.22"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
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
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*",
              "hint": "unknown hint"
            }
          ]
        }
      ]
    },


    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Translate",
        "subprocid": "TranslateTiles",
        "version": "0.9.0",
        "minuserstratum": 5,
        "title": "Translate tiles using gdal_translate"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6842,
          "dstepsg": 6842
        },
        {
          "system": "landsat",
          "srcsystem": "landsat",
          "dstsystem": "landsat",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 3200,
          "dstepsg": 3200
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
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "dstEPSG",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "xoff",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "yoff",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "xsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "ysize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "tr_xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "tr_yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "resample",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "near"
            },
            {
              "paramid": "autofitextent",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "src_min",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "src_max",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_min",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_max",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "exponent",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "unscale",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "dst_ulx",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_uly",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_lrx",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "dst_lry",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.0"
            },
            {
              "paramid": "nodata",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "-22.22"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
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
              "hint": "Import layer suffix (usually identical to id)"
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
              "required": true,
              "defaultvalue": "*",
              "hint": "unknown hint"
            }
          ]
        }
      ]
    }
  ]
}
```
