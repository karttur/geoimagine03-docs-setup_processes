---
layout: article
title: DEMnumpyProc_v090.json
categories: setup_processes
excerpt:  Install processes for DEM data using numpy
tags:: 
    - json/DEMnumpyProc
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/DEMnumpyProc (setup_processes)

###  Install processes for DEM data using numpy

The json command file <span class='file'>DEMnumpyProc_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "NumpyProc",
        "title": "Numpy data processing",
        "label": "Various processing relying on Numpy"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "NumpyProc",
        "subprocid": "NumpyDemRegion",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Generate DEM derivates",
        "label": "Generate DEM derivates using numpy."
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
                  "value": "smooth",
                  "label": "smooth"
                },
                {
                  "value": "slope",
                  "label": "slope"
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
                  "value": "bluntTPI",
                  "label": "Topographic Position Index"
                },
                {
                  "value": "roughness",
                  "label": "roughness"
                }
              ]
            },
            {
              "paramid": "trigonometric",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Trigonometric measure for slope or not."
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
              "paramid": "kernelform",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "square",
              "hint": "Kernel from",
              "setvalue": [
                {
                  "value": "square",
                  "label": "Ordinary square kernel"
                },
                {
                  "value": "round",
                  "label": "kernel with rounded edges"
                },
                {
                  "value": "skewedNS",
                  "label": "skewed North_South"
                },
                {
                  "value": "skewedEW",
                  "label": "skewed East-West"
                },
                {
                  "value": "skewedNwSe",
                  "label": "skewed Northwest - Southeast"
                },
                {
                  "value": "skewedNeSw",
                  "label": "skewed Northeast - Southwest"
                }
              ]
            },
            {
              "paramid": "kernelvalues",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "equal",
              "hint": "Kernel value range",
              "setvalue": [
                {
                  "value": "equal",
                  "label": "All kernel active cells=1"
                },
                {
                  "value": "decline",
                  "label": "values decline byy half away from center"
                },
                {
                  "value": "increase",
                  "label": "values double by distance from center"
                }
              ]
            },
            {
              "paramid": "standardize",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Standardize or not."
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Palette."
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
        "rootprocid": "NumpyProc",
        "subprocid": "NumpyGeomorphology",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Extract Geomorphology from multilayers",
        "label": "Extract Geomorphology from multilayers."
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
              "defaultvalue": "weiss",
              "setvalue": [
                {
                  "value": "weiss",
                  "label": "Weiss original"
                }
              ]
            },
            {
              "paramid": "standardize",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Standardize or not."
            },
            {
              "paramid": "detailedTPIstd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 30,
              "hint": "Global standard deviation for detailed TPI"
            },
            {
              "paramid": "bluntTPIstd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 50,
              "hint": "Global standard deviation for blunt TPI"
            },
            {
              "paramid": "slopethreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1,
              "hint": "slope threshold"
            },
            {
              "paramid": "tpithreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 5,
              "hint": "TPI threshold"
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Palette."
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
              "paramid": "detailedTPI",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "detailedTPI",
              "hint": "link for source composition detailed TPI"
            },
            {
              "paramid": "bluntTPI",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "bluntTPI",
              "hint": "link for source composition blunt TPI"
            },
            {
              "paramid": "slope",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "slope",
              "hint": "link for source composition slope"
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
              "defaultvalue": "bluntTPI",
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
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "class",
              "hint": "unknown hint"
            },
            {
              "paramid": "cellnull",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 255,
              "hint": "unknown hint"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Byte",
              "hint": "unknown hint"
            }
          ]
        }
      ]
    },
    {
      "processid": "addrootproc",
      "parameters": {
        "rootprocid": "NumpyProc",
        "title": "Numpy data processing",
        "label": "Various processing relying on Numpy"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "NumpyProc",
        "subprocid": "NumpyDemTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Generate DEM derivates",
        "label": "Generate DEM derivates using numpy."
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
                  "value": "smooth",
                  "label": "smooth"
                },
                {
                  "value": "slope",
                  "label": "slope"
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
                  "value": "landformTPI",
                  "label": "Landform from Topographic Position Index "
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
              "defaultvalue": true
            },
            {
              "paramid": "trigonometric",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Trigonometric measure for slope or not."
            },
            {
              "paramid": "kernelform",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "square",
              "hint": "Kernel from",
              "setvalue": [
                {
                  "value": "square",
                  "label": "Ordinary square kernel"
                },
                {
                  "value": "round",
                  "label": "kernel with rounded edges"
                },
                {
                  "value": "skewedNS",
                  "label": "skewed North_South"
                },
                {
                  "value": "skewedEW",
                  "label": "skewed East-West"
                },
                {
                  "value": "skewedNwSe",
                  "label": "skewed Northwest - Southeast"
                },
                {
                  "value": "skewedNeSw",
                  "label": "skewed Northeast - Southwest"
                }
              ]
            },
            {
              "paramid": "kernelvalues",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "equal",
              "hint": "Kernel value range",
              "setvalue": [
                {
                  "value": "equal",
                  "label": "All kernel active cells=1"
                },
                {
                  "value": "decline",
                  "label": "values decline byy half away from center"
                },
                {
                  "value": "increase",
                  "label": "values double by distance from center"
                }
              ]
            },
            {
              "paramid": "standardize",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Standardize or not."
            },
            {
              "paramid": "tpithreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 5,
              "hint": "TPI threshold."
            },
            {
              "paramid": "slopethreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1,
              "hint": "slope threshold."
            },
            {
              "paramid": "dtpistd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 25,
              "hint": "default std for detailed TPI."
            },
            {
              "paramid": "btpistd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 50,
              "hint": "default std for blunt TPI."
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Palette."
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
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "NumpyProc",
        "subprocid": "NumpyGeomorphologyTiles",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Extract Geomorphology from multilayers",
        "label": "Extract Geomorphology from multilayers."
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
              "defaultvalue": "weiss",
              "setvalue": [
                {
                  "value": "weiss",
                  "label": "Weiss original"
                }
              ]
            },
            {
              "paramid": "standardize",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Standardize or not."
            },
            {
              "paramid": "slopethreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1,
              "hint": "slope threshold"
            },
            {
              "paramid": "tpithreshold",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 5,
              "hint": "TPI threshold"
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
              "defaultvalue": "1,3",
              "hint": "radius sizes separated with commas"
            },
            {
              "paramid": "compute_edges",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Palette."
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
