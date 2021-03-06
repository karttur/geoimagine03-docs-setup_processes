---
layout: article
title: modisProcess_v090.json
categories: setup_processes
excerpt:  Install MODIS specific processing
tags:: 
    - json/modisProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/modisProcess (setup_processes)

###  Install MODIS specific processing

The json command file <span class='file'>modisProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "subprocid": "ExplodeMODISRegion",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Extracts the content of modis scenes",
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
              "paramid": "exploded",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False",
              "hint": "to be completed"
            },
            {
              "paramid": "asscript",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True",
              "hint": "to be completed"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "to be completed",
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
        "subprocid": "MissingModisTiles",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Copies closest neighboring tile to missing",
        "label": "Copies closest neighboring tile to missing"
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
              "paramid": "source",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "masked",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "Y"
            }
          ]
        },
        {
          "parent": "process",
          "element": "srcband",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "prefix",
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
        "subprocid": "resampleSpatialModisRegion",
        "version": "1.3",
        "minuserstratum": "5",
        "title": "Tile regional SMAP data to fit modis",
        "label": "Tile regional SMAP data to fit modis"
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
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "epsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "6842"
            },
            {
              "paramid": "xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "463.313"
            },
            {
              "paramid": "yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "463.313"
            },
            {
              "paramid": "resample",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "near"
            },
            {
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1to1"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "copy"
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
          "parent": "srccomp",
          "element": "*",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "region"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "system",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "smap"
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
        "subprocid": "MosaicModis",
        "version": "1.3",
        "minuserstratum": "5",
        "title": "Mosaic mdois raster tiles to region"
      },
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
              "paramid": "overlay",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "mean"
            },
            {
              "paramid": "t_epsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "resample",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "near"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "export",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "movieframes",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1to1"
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
          "parent": "srccomp",
          "element": "*",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "region"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            }
          ]
        }
      ],
      "system": [
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "modis",
          "srcdivision": "tiles",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "MODISProc",
        "subprocid": "MosaicModisExport",
        "version": "1.3",
        "minuserstratum": "5",
        "title": "Mosaic mdois raster tiles to region"
      },
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
              "paramid": "overlay",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "mean"
            },
            {
              "paramid": "t_epsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "resample",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "near"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "auto"
            },
            {
              "paramid": "export",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "movieframes",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1to1"
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
          "parent": "srccomp",
          "element": "*",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "region"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "system",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "ancillary"
            }
          ]
        }
      ],
      "system": [
        {
          "system": "export",
          "srcsystem": "export",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        }
      ]
    }
  ],
  "processx": {
    "processid": "addsubproc",
    "overwrite": false,
    "parameters": {
      "rootprocid": "MODISProc",
      "subprocid": "Modisregion",
      "version": "0.8.0",
      "minuserstratum": 10,
      "title": "manage MODIS regions",
      "label": "Link MODIS tiles to existing region (default region, tract or site). "
    },
    "nodes": [
      {
        "parent": "process",
        "element": "parameters"
      },
      {
        "parent": "process",
        "element": "srccomp",
        "parameter": {
          "paramid": "content",
          "paramtyp": "text",
          "required": false,
          "defaultvalue": "modisregion"
        }
      }
    ]
  }
}
```
