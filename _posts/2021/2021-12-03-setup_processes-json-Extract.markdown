---
layout: article
title: Extract_v090.json
categories: setup_processes
excerpt:  Install process for extracting raster stats under vector data
tags:: 
    - json/Extract
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/Extract (setup_processes)

###  Install process for extracting raster stats under vector data

The json command file <span class='file'>Extract_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "delete": false,
      "parameters": {
        "rootprocid": "Extract",
        "title": "Extract raster statistics",
        "label": "Extract raster statistics"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": false,
      "parameters": {
        "rootprocid": "Extract",
        "subprocid": "ExtractTilesPointList",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Extract raster data for listed coordinates",
        "label": "Extract raster data for listed coordinates"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6842,
          "dstepsg": 0
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6932,
          "dstepsg": 0
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6933,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "coordlistfilepath",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "full path to file listing coordinates"
            },
            {
              "paramid": "kernelsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "mean",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "std",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "range",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "minimum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "maximum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "mode",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
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
              "required": true,
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
              "required": true,
              "defaultvalue": "csv"
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
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": false,
      "parameters": {
        "rootprocid": "Extract",
        "subprocid": "ExtractTilesPointVector",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Extract raster data for listed coordinates",
        "label": "Extract raster data for listed coordinates"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6842,
          "dstepsg": 0
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6932,
          "dstepsg": 0
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6933,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "kernelsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "mean",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "std",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "range",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "minimum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "maximum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "mode",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
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
              "required": true,
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
              "required": true,
              "defaultvalue": "csv"
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
          "parent": "srccomp",
          "element": "vector",
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
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "ext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "csv",
              "hint": "File typae for savning extracted raster stats"
            }
          ]
        }
      ]
    },

    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": false,
      "parameters": {
        "rootprocid": "Extract",
        "subprocid": "ExtractTilesLineVector",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Extract raster data for listed coordinates",
        "label": "Extract raster data for listed coordinates"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6842,
          "dstepsg": 0
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6932,
          "dstepsg": 0
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6933,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [

            {
              "paramid": "mean",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "std",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "range",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "minimum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "maximum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "mode",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
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
              "required": true,
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
              "required": true,
              "defaultvalue": "csv"
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
          "parent": "srccomp",
          "element": "vector",
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
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "ext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "csv",
              "hint": "File typae for savning extracted raster stats"
            }
          ]
        }
      ]
    },

    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": false,
      "parameters": {
        "rootprocid": "Extract",
        "subprocid": "ExtractTilesPolyVector",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Extract raster data for listed coordinates",
        "label": "Extract raster data for listed coordinates"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6842,
          "dstepsg": 0
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6932,
          "dstepsg": 0
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 6933,
          "dstepsg": 0
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [

            {
              "paramid": "mean",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "std",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "range",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "minimum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "maximum",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "mode",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
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
              "required": true,
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
              "required": true,
              "defaultvalue": "csv"
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
          "parent": "srccomp",
          "element": "vector",
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
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy",
              "hint": "unknown hint"
            },
            {
              "paramid": "ext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "csv",
              "hint": "File typae for savning extracted raster stats"
            }
          ]
        }
      ]
    }

  ]
}
```
