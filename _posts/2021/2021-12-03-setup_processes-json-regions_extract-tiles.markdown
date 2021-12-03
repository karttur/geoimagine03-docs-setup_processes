---
layout: article
title: regions_extract-tiles_v090.json
categories: setup_processes
excerpt:  Install processes for extracing tile corners
tags:: 
    - json/regions_extract-tiles
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions extract tiles (setup_processes)

###  Install processes for extracing tile corners

The json command file <span class='file'>regions_extract-tiles_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "ExtractTileCoords",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Extract tile coordinates",
        "label": "Extract tile coordinates and add to db"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "ancillary",
          "dstsystem": "sentinel",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "landsat",
          "srcsystem": "ancillary",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "modis",
          "srcsystem": "ancillary",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2n",
          "srcsystem": "ancillary",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ancillary",
          "dstsystem": "ease2s",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 6932
        },
        {
          "system": "ease2t",
          "srcsystem": "ancillary",
          "dstsystem": "ease2t",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 6933
        },
        {
          "system": "sweref",
          "srcsystem": "ancillary",
          "dstsystem": "sweref",
          "srcdivision": "region",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 3006
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "centroid",
              "paramtyp": "bool",
              "required": true,
              "defaultvalue": "True"
            },
            {
              "paramid": "mgrs",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "MGRS"
            },
            {
              "paramid": "gzd",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "GZD"
            },
            {
              "paramid": "utmzone",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "ZONE"
            },
            {
              "paramid": "utmzone",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "wrspath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "PATH"
            },
            {
              "paramid": "wrsrow",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "ROW"
            },
            {
              "paramid": "wrsmode",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "MODE"
            },
            {
              "paramid": "wrs",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2
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
              "defaultvalue": "shp"
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
              "defaultvalue": "vector"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "vector"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "vector"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            }
          ]
        }
      ]
    }
  ]
}
```
