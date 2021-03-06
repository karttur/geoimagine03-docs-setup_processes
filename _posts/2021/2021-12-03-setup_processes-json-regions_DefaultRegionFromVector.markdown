---
layout: article
title: regions_DefaultRegionFromVector_v090.json
categories: setup_processes
excerpt:  Install sub process DefaultRegionFromVector
tags:: 
    - json/regions_DefaultRegionFromVector
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions DefaultRegionFromVector (setup_processes)

###  Install sub process DefaultRegionFromVector

The json command file <span class='file'>regions_DefaultRegionFromVector_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "ManageRegion",
        "subprocid": "DefaultRegionFromVector",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Define default region from vector data set",
        "label": "Only superuser can set default regions, send request it you really need a new default region category"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "system",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6933
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "system",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
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
              "paramid": "vector_db_id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "ISO_A3",
              "hint": "Column in source vector db that defines default region id"
            },
            {
              "paramid": "vector_db_name",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "NAME",
              "hint": "Column in source vector db that defines default region name"
            },
            {
              "paramid": "vector_db_category",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Column in source vector db that defines default region category"
            },
            {
              "paramid": "vector_db_parentid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "PARENTID",
              "hint": "Column in source vector db that defines default region parent id"
            },
            {
              "paramid": "vector_db_parentcat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "PARENTCAT",
              "hint": "Column in source vector db that defines default region parent category"
            },
            {
              "paramid": "vector_db_stratum",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "STRATUM",
              "hint": "Column in source vector db that defines default region pstratum"
            },
            {
              "paramid": "vector_db_title",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "TITLE",
              "hint": "Column in source vector db that defines default region title"
            },
            {
              "paramid": "vector_db_label",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "LABEL",
              "hint": "Column in source vector db that defines default region label"
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "1.0",
              "hint": "Default region version"
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
              "hint": "Volume or disk"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "shp",
              "hint": "Source vector data format"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "na",
              "hint": "Data file extension for datasets with separate header + data file"
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
              "hint": "Volume or disk"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "shp",
              "hint": "Header or header+data file extension"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "tagorattr": "Attr",
              "required": true,
              "defaultvalue": "na",
              "hint": "Data file extension for datasets with separate header + data file"
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
              "hint": "Hierarchical object parent (for internal use)"
            },
            {
              "paramid": "element",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "Default hierarchical child name"
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
              "hint": "Dataset source (e.g. sensor, method, model, etc (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Dataset type, product, producer etc  (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Dataset content (hyphen allowed, underscore not allowd)"
            },
            {
              "paramid": "layerid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "srcdefregvec",
              "hint": "Dataset layer or band id"
            },
            {
              "paramid": "prefix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "File name prefix"
            },
            {
              "paramid": "suffix",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Additional identifier, e.g. version or model etc (hyphen allowed, underscore not allowed)"
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
        },
        {
          "parent": "dstcopy",
          "element": "*",
          "parameter": [
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
