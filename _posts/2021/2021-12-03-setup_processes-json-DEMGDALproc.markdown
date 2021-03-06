---
layout: article
title: DEMGDALproc_v090.json
categories: setup_processes
excerpt:  Install processes for DEM data using GDAL
tags:: 
    - json/DEMGDALproc
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/DEMGDALproc (setup_processes)

###  Install processes for DEM data using GDAL

The json command file <span class='file'>DEMGDALproc_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "DemProc",
        "title": "DEM data processing",
        "label": "Processes of Digital Elevation Models (DEMs)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DemProc",
        "subprocid": "GdalDemRegion",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Generate DEM derivates",
        "label": "Generate DEM derivates using gdaldem."
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
              "paramid": "mode",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "slope",
              "setvalue": [
                {
                  "value": "slope",
                  "label": "slope"
                },
                {
                  "value": "aspect",
                  "label": "aspect"
                },
                {
                  "value": "hillshade",
                  "label": "hillshade"
                },
                {
                  "value": "color-relief",
                  "label": "color-relief"
                },
                {
                  "value": "TRI",
                  "label": "Terrain Ruggedness Index"
                },
                {
                  "value": "TPI",
                  "label": "Topographic Position Index"
                },
                {
                  "value": "roughness",
                  "label": "roughness"
                }
              ]
            },
            {
              "paramid": "compute_edges",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "trigonometric",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Trigonometric measure for slope and azimuth or not."
            },
            {
              "paramid": "azimuth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 315,
              "hint": "azimuth value for hillshading"
            },
            {
              "paramid": "altitude",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 45,
              "hint": "altitude value for hillshading"
            },
            {
              "paramid": "zfac",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1,
              "hint": "z factor for hillshading"
            },
            {
              "paramid": "algorithm",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Algorithm for slope",
              "setvalue": [
                {
                  "value": "ZevenbergenThorne",
                  "label": "For smooth terrain"
                },
                {
                  "value": "Horn",
                  "label": "For rough terrain"
                }
              ]
            },
            {
              "paramid": "zero_for_flat",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true,
              "hint": "flat=0 if true, otherwise -9999"
            },
            {
              "paramid": "color_text_file",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "full path to color text file"
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
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
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DemProc",
        "subprocid": "GdalDemTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Generate DEM derivates",
        "label": "Generate DEM derivates using gdaldem."
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
              "paramid": "mode",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "slope",
              "setvalue": [
                {
                  "value": "slope",
                  "label": "slope"
                },
                {
                  "value": "aspect",
                  "label": "aspect"
                },
                {
                  "value": "hillshade",
                  "label": "hillshade"
                },
                {
                  "value": "color-relief",
                  "label": "color-relief"
                },
                {
                  "value": "TRI",
                  "label": "Terrain Ruggedness Index"
                },
                {
                  "value": "TPI",
                  "label": "Topographic Position Index"
                },
                {
                  "value": "roughness",
                  "label": "roughness"
                }
              ]
            },
            {
              "paramid": "mosaic",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "radiuscsv",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1",
              "hint": "radius sizes separated with commas"
            },
            {
              "paramid": "compute_edges",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "trigonometric",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Trigonometric measure for slope and azimuth or not."
            },
            {
              "paramid": "azimuth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 315,
              "hint": "azimuth value for hillshading"
            },
            {
              "paramid": "altitude",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 45,
              "hint": "altitude value for hillshading"
            },
            {
              "paramid": "zfac",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1,
              "hint": "z factor for hillshading"
            },
            {
              "paramid": "algorithm",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Algorithm for slope",
              "setvalue": [
                {
                  "value": "ZevenbergenThorne",
                  "label": "For smooth terrain"
                },
                {
                  "value": "Horn",
                  "label": "For rough terrain"
                }
              ]
            },
            {
              "paramid": "zero_for_flat",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true,
              "hint": "flat=0 if true, otherwise -9999"
            },
            {
              "paramid": "color_text_file",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "full path to color text file"
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
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
            },
            {
              "paramid": "dataunit",
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
