---
layout: article
title: regions-DefaultRegionFromCoords_v090.json
categories: setup_processes
excerpt:  Install sub process DefaultRegionFromLonLat
tags:: 
    - json/regions-DefaultRegionFromCoords
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions DefaultRegionFromCoords (setup_processes)

###  Install sub process DefaultRegionFromLonLat

The json command file <span class='file'>regions-DefaultRegionFromCoords_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

```
{
  "process": [
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "DefaultRegionFromCoords",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Define default region for public use from corner coordinates",
        "label": "Only superuser can set default regions, send request it you really need a new default region category"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "NA",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "modis",
          "srcsystem": "NA",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2t",
          "srcsystem": "NA",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6933
        },
        {
          "system": "ease2n",
          "srcsystem": "NA",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "NA",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6932
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "regionid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Set an id for the default region"
            },
            {
              "paramid": "regionname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Default region name (must be unique)"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Default region category",
              "setvalue": [
                {
                  "value": "global",
                  "label": "global region"
                },
                {
                  "value": "continental",
                  "label": "continental region"
                },
                {
                  "value": "subcontinental",
                  "label": "subcontinental region"
                },
                {
                  "value": "basin",
                  "label": "Hydrological river basin region"
                },
                {
                  "value": "sovereign",
                  "label": "Soverign country region"
                },
                {
                  "value": "country",
                  "label": "Country national region"
                },
                {
                  "value": "state",
                  "label": "statel level region"
                },
                {
                  "value": "district",
                  "label": "district region"
                },
                {
                  "value": "community",
                  "label": "community region"
                },
                {
                  "value": "tract",
                  "label": "tract (user defined) region"
                },
                {
                  "value": "site",
                  "label": "site (user defined) region"
                }
              ]
            },
            {
              "paramid": "parentid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Default region parent regionid"
            },
            {
              "paramid": "parentcat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Default region parent region category"
            },
            {
              "paramid": "stratum",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0,
              "hint": "Stratum for region access",
              "minmax": {
                "min": 0,
                "max": 12
              }
            },
            {
              "paramid": "minx",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": 0,
              "hint": "x-coord or longitude minimum",
              "minmax": {
                "min": -90,
                "max": 90
              }
            },
            {
              "paramid": "maxx",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": 0,
              "hint": "x-coord or longitude maximum",
              "minmax": {
                "min": -90,
                "max": 90
              }
            },
            {
              "paramid": "miny",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": 0,
              "hint": "y-coord or latitude minimum",
              "minmax": {
                "min": -180,
                "max": 180
              }
            },
            {
              "paramid": "maxy",
              "paramtyp": "float",
              "required": true,
              "defaultvalue": 0,
              "hint": "y-coord or latitude maximum",
              "minmax": {
                "min": -180,
                "max": 180
              }
            },
            {
              "paramid": "epsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "4326",
              "hint": "EPSG code for region"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.0",
              "hint": "Region version"
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Title",
              "hint": "Region title"
            },
            {
              "paramid": "label",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Label",
              "hint": "Region label"
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
              "paramid": "*",
              "paramtyp": "element",
              "required": false,
              "defaultvalue": "*",
              "hint": "1:1 link for destination composition"
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
              "hint": "File name prefix"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v010",
              "hint": "Additional identifier, e.g. version or model etc (hyphen allowed, underscore not allowed)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "Nominal (boundary)"
            },
            {
              "paramid": "masked",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "hint": "not applicable"
            },
            {
              "paramid": "cellnull",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0",
              "hint": "not applicable"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "vector",
              "hint": "vector"
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
        }
      ]
    }
  ]
}
```
