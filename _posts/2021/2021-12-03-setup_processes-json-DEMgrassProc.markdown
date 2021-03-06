---
layout: article
title: DEMgrassProc_v090.json
categories: setup_processes
excerpt:  Install processes for DEM data using GRASS GIS
tags:: 
    - json/DEMgrassProc
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/DEMgrassProc (setup_processes)

###  Install processes for DEM data using GRASS GIS

The json command file <span class='file'>DEMgrassProc_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "GrassDemProc",
        "title": "Grass data processing",
        "label": "Various processing relying on GRASS"
      }
    },
    {
      "processid": "addsubproc",
      "delete": true,
      "parameters": {
        "rootprocid": "GrassDemProc",
        "subprocid": "GrassDemPitFillRegions",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Fill up dem pits",
        "label": "Fill up dem pits with GRASS r.fill.dir or r.hydrodem."
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
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
          "dstdivision": "region",
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
              "paramid": "superimpose",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "pitflags",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "memory",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "300",
              "hint": "Maximum memory to be used in MB."
            },
            {
              "paramid": "pitmod",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4,
              "hint": "Only remove sinks requiring not more than <mod> cell modifications."
            },
            {
              "paramid": "pitsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4,
              "hint": "Only remove sinks not larger than <size> cells"
            },
            {
              "paramid": "pitquery",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Query for filling pits"
            },
            {
              "paramid": "peaks",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False",
              "hint": "Remove single peaks or not."
            },
            {
              "paramid": "peakquery",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Query for filling pits"
            },
            {
              "paramid": "tilesize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1000,
              "hint": "Tile size (pixels) for dividing DEM raster"
            },
            {
              "paramid": "tileoverlap",
              "paramtyp": "itneger",
              "required": false,
              "defaultvalue": 10,
              "hint": "Tile overlap for dividing DEM raster "
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
            },
            {
              "paramid": "prefix",
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
        "rootprocid": "GrassDemProc",
        "subprocid": "GrassDemFillDirTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Fill up dem pits",
        "label": "Fill up dem pits with GRASS r.fill.dir."
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
              "paramid": "superimpose",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "mosaic",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "memory",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300
            },
            {
              "paramid": "pitsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4,
              "hint": "Only remove sinks not larger than <pitsize> cells"
            },
            {
              "paramid": "pitburnattribute",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "filldem",
              "hint": "Attribute to use for burning DEM"
            },
            {
              "paramid": "pitquery",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Query for filling pits"
            },
            {
              "paramid": "peaks",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False",
              "hint": "Remove single peaks or not."
            },
            {
              "paramid": "peakburnattribute",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "nbdemq1",
              "hint": "Attribute to use for burning DEM"
            },
            {
              "paramid": "peakquery",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Query for flattening peaks"
            },
            {
              "paramid": "tilesize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1000,
              "hint": "Tile size (pixels) for dividing DEM raster"
            },
            {
              "paramid": "tileoverlap",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10,
              "hint": "Tile overlap for dividing DEM raster "
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
            },
            {
              "paramid": "prefix",
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
        "rootprocid": "GrassDemProc",
        "subprocid": "GrassDemHydroDemTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Fill up dem pits",
        "label": "Fill up dem pits with GRASS r.hydrodem."
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
              "paramid": "superimpose",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "mosaic",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "flags",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "size",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4,
              "hint": "Only remove sinks not larger than <size> cells"
            },
            {
              "paramid": "mod",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4,
              "hint": ""
            },
            {
              "paramid": "diffthreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0.01,
              "hint": "min difference original DEM and HydroDEM to count as change"
            },
            {
              "paramid": "query",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Query for burning hydrodem corrections"
            },
            {
              "paramid": "memory",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300,
              "hint": "Memory allocation"
            },
            {
              "paramid": "tilesize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1000,
              "hint": "Tile size (pixels) for dividing DEM raster"
            },
            {
              "paramid": "tileoverlap",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10,
              "hint": "Tile overlap for dividing DEM raster "
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
            },
            {
              "paramid": "prefix",
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
        "rootprocid": "GrassDemProc",
        "subprocid": "GrassDemReInterpolateTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Fill up dem pits",
        "label": "Resample DEM with r.resamp.rst."
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
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "mosaic",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "flags",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "4",
              "hint": "flags for r.resamp.rst"
            },
            {
              "paramid": "ew_res",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "x resolutin 0 = same as imput"
            },
            {
              "paramid": "ns_res",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "x resolutin 0 = same as imput"
            },
            {
              "paramid": "overlap",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 3,
              "hint": "Rows/columns overlap for segmentation"
            },
            {
              "paramid": "tension",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 40,
              "hint": "Spline tension value"
            },
            {
              "paramid": "tilesize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1000,
              "hint": "Tile size (pixels) for dividing DEM raster"
            },
            {
              "paramid": "tileoverlap",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10,
              "hint": "Tile overlap for dividing DEM raster "
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
            },
            {
              "paramid": "prefix",
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
