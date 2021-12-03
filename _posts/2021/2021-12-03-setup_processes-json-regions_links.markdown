---
layout: article
title: regions_links_v090.json
categories: setup_processes
excerpt:  Install processes for linking regions to tiles
tags:: 
    - json/regions_links
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions links (setup_processes)

###  Install processes for linking regions to tiles

The json command file <span class='file'>regions_links_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
  "period": {
    "timestep": "static"
  },
  "process": [
    {
      "processid": "addsubproc",
      "overwrite": true,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "LinkDefaultRegionTiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Link Default Regions to system tiles",
        "label": "Link Default Regions to system tiles"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "system",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2n",
          "srcsystem": "system",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "system",
          "dstsystem": "ease2s",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6932
        },
        {
          "system": "ease2t",
          "srcsystem": "system",
          "dstsystem": "ease2t",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6933
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "defregmask",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "land",
              "hint": "Default region for restricting tile search"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
            },
            {
              "paramid": "checkfixvalidity",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": true,
              "hint": "check and fix validty of simplifed vector before saving"
            },
            {
              "paramid": "onlyregionsfullywithinsystem",
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
              "defaultvalue": "",
              "hint": "to be completed"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
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
              "defaultvalue": ""
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp"
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
              "hint": "Hierarchical pointer"
            },
            {
              "paramid": "parent",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "process",
              "hint": "to be completed"
            },
            {
              "paramid": "element",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
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
              "defaultvalue": "karttur",
              "hint": "Dataset source (e.g. sensor, method, model, etc (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "pubroi",
              "hint": "Dataset type, product, producer etc  (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Dataset content (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "Dataset layer or band id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v010",
              "hint": "to be completed"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "region",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "region",
              "hint": "link for destination composition"
            }
          ]
        },
        {
          "parent": "dstcomp",
          "element": "region",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "karttur",
              "hint": "Source instrument, method, model or similar of import layer (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "region",
              "hint": "Import layer product, producer or similary (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Import layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Destination data scale measure"
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
              "required": false,
              "defaultvalue": "0",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "vector",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)"
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
              "required": false,
              "defaultvalue": "boundary",
              "hint": "Data unit for raster cell data"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "tiles",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "tiles",
              "hint": "link for destination composition"
            }
          ]
        },
        {
          "parent": "dstcomp",
          "element": "tiles",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "karttur",
              "hint": "Source instrument, method, model or similar of import layer (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tiles",
              "hint": "Import layer product, producer or similary (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Import layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tiles",
              "hint": "Import layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Destination data scale measure"
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
              "required": false,
              "defaultvalue": "0",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "vector",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)"
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
              "required": false,
              "defaultvalue": "tile",
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
        "rootprocid": "ManageRegion",
        "subprocid": "LinkDefaultRegionScenes",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Link Default Regions to system scenes",
        "label": "Link Default Regions to system scenes"
      },
      "system": [
        {
          "system": "landsat",
          "srcsystem": "landsat",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "none",
          "srcepsg": 4326,
          "dstepsg": 4326
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "wrs",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2,
              "hint": "WRS 1 or 2 (default=2)"
            },
            {
              "paramid": "dir",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "D",
              "hint": "Descent or Ascent (default=Descent)"
            },
            {
              "paramid": "minarea",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "Minimum overlap area of region and scene for linking"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
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
              "defaultvalue": "shp",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "to be completed"
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
              "hint": "Hierarchical pointer"
            },
            {
              "paramid": "parent",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "process",
              "hint": "to be completed"
            },
            {
              "paramid": "element",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
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
              "defaultvalue": "karttur",
              "hint": "Dataset source (e.g. sensor, method, model, etc (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "pubroi",
              "hint": "Dataset type, product, producer etc  (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Dataset content (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "Dataset layer or band id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v010",
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
        "rootprocid": "ManageRegion",
        "subprocid": "LinkSingleRegionScenes",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Link Single Region to system scenes",
        "label": "Link Single Region to system scenes"
      },
      "system": [
        {
          "system": "landsat",
          "srcsystem": "landsat",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "none",
          "srcepsg": 4326,
          "dstepsg": 4326
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "defregmask",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None",
              "hint": "Default region for restricting tile search, default: None"
            },
            {
              "paramid": "wrs",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2,
              "hint": "WRS 1 or 2 (default=2)"
            },
            {
              "paramid": "dir",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "D",
              "hint": "Descent or Ascent (default=Descent)"
            },
            {
              "paramid": "minarea",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "Minimum overlap area of region and scene for linking"
            },
            {
              "paramid": "regionid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "globalland",
              "hint": "Name of single region"
            },
            {
              "paramid": "regiontype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Region type [default, tract, site]"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
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
              "defaultvalue": "shp",
              "hint": "to be completed"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "to be completed"
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
              "hint": "Hierarchical pointer"
            },
            {
              "paramid": "parent",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "process",
              "hint": "to be completed"
            },
            {
              "paramid": "element",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "to be completed"
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
              "defaultvalue": "karttur",
              "hint": "Dataset source (e.g. sensor, method, model, etc (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "pubroi",
              "hint": "Dataset type, product, producer etc  (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Dataset content (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "Dataset layer or band id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "defreg",
              "hint": "to be completed"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v010",
              "hint": "to be completed"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": true,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "VectorizeRegionTiling",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Export a region and its tiles as vectors",
        "label": "Export a region and its tiles as vectors"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "system",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 4326,
          "dstepsg": 6842
        },
        {
          "system": "ease2n",
          "srcsystem": "system",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 4326,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "system",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 4326,
          "dstepsg": 6932
        },
        {
          "system": "ease2t",
          "srcsystem": "system",
          "dstsystem": "ease2t",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 4326,
          "dstepsg": 6933
        },
        {
          "system": "landsat",
          "srcsystem": "system",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 4326,
          "dstepsg": 4326
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "asscript",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*"
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
              "defaultvalue": "shp"
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
              "defaultvalue": "shp"
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
              "hint": "layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "*",
              "hint": "layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "layer suffix (usually identical to id)"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "region",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "region",
              "hint": "link for destination composition"
            }
          ]
        },
        {
          "parent": "dstcomp",
          "element": "region",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "karttur",
              "hint": "Source instrument, method, model or similar of import layer (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "region",
              "hint": "Import layer product, producer or similary (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Import layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Destination data scale measure"
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
              "required": false,
              "defaultvalue": "0",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "vector",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)"
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
              "required": false,
              "defaultvalue": "boundary",
              "hint": "Data unit for raster cell data"
            }
          ]
        },
        {
          "parent": "process",
          "element": "dstcomp",
          "parameter": [
            {
              "paramid": "tiles",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "tiles",
              "hint": "link for destination composition"
            }
          ]
        },
        {
          "parent": "dstcomp",
          "element": "tiles",
          "parameter": [
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "karttur",
              "hint": "Source instrument, method, model or similar of import layer (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tiles",
              "hint": "Import layer product, producer or similary (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "roi",
              "hint": "Import layer content or theme (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tiles",
              "hint": "Import layer id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default",
              "hint": "Import layer prefix (usually identical to layerid)"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Destination data scale measure"
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
              "required": false,
              "defaultvalue": "0",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "vector",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)"
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
              "required": false,
              "defaultvalue": "tile",
              "hint": "Data unit for raster cell data"
            }
          ]
        }
      ]
    }
  ]
}
```
