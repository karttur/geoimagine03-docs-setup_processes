---
layout: article
title: ancillary_root+organize_v090.json
categories: setup_processes
excerpt:  Install ancillary root + OrganizeAncillary processing
tags:: 
    - json/ancillary_root+organize
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/ancillary root+organize (setup_processes)

###  Install ancillary root + OrganizeAncillary processing

The json command file <span class='file'>ancillary_root+organize_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "Ancillary",
        "title": "Ancillary data processing",
        "label": "Processes for downloading and organizing ancillary data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Ancillary",
        "subprocid": "OrganizeAncillary",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Organize ancillary data",
        "label": "Organize local (downloaded or created) ancillary data"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "NA",
          "dstsystem": "ancillary",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "specimen",
          "srcsystem": "NA",
          "dstsystem": "specimen",
          "srcdivision": "NA",
          "dstdivision": "NA",
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
              "paramid": "importcode",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "tif",
              "hint": "Import code that identifies whith subroutine to use for import",
              "setvalue": [
                {
                  "value": "viewer",
                  "label": "view user"
                }
              ]
            },
            {
              "paramid": "epsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 4326,
              "hint": "EPSG 4-integer code of projection for dataset to import"
            },
            {
              "paramid": "orgid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Organisation id for dataset"
            },
            {
              "paramid": "dsname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Name of dataset to import"
            },
            {
              "paramid": "dsversion",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0",
              "hint": "Dataset version (if applicable)"
            },
            {
              "paramid": "accessdate",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Date of accessing dataset (if left blank todays date will be recorded)"
            },
            {
              "paramid": "regionid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Default region id of the dataset"
            },
            {
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Region category of the dataset"
            },
            {
              "paramid": "dataurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "url for source dataset"
            },
            {
              "paramid": "metaurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "url for source metadata"
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Source dataset title"
            },
            {
              "paramid": "label",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Source dataset label"
            },
            {
              "paramid": "copyright",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "unknown",
              "hint": "Source dataset copyright"
            },
            {
              "paramid": "replacestr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "String to replace in multi-layered source datasets"
            },
            {
              "paramid": "replacetag",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Tag identifying replacement identifying"
            },
            {
              "paramid": "tolerance",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "tolerance for simplifying vectors using distance"
            },
            {
              "paramid": "angletolerance",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "tolerance for simplifying vectors using angles"
            },
            {
              "paramid": "quadrangle",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": false,
              "hint": "simplify vector polytgon to quadrangle"
            },

            {
              "paramid": "checkfixvalidity",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": true,
              "hint": "check and fix validty of simplifed vector before saving"
            },

            {
              "paramid": "fieldNameDstL",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "Comma separated name(s) of vector field names to copy"
            },
            {
              "paramid": "attribFilter",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Attribute filter to apply for feature copying"
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
              "hint": "Volume, disk or path containg the source data"
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Header or header+data file extension"
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
          "element": "srcraw",
          "parameter": [
            {
              "paramid": "*",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "*",
              "hint": "link for srcraw composition"
            }
          ]
        },
        {
          "parent": "srcraw",
          "element": "*",
          "parameter": [
            {
              "paramid": "datadir",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Source data local directory (under volume)"
            },
            {
              "paramid": "datafile",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Source data file name"
            },
            {
              "paramid": "datalayer",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Source data layer name"
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Source dataset title"
            },
            {
              "paramid": "label",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Label for import data set",
              "hint": "Source dataset label"
            },
            {
              "paramid": "cellnull",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 2222.2,
              "hint": "Cell null for raster data"
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
              "required": true,
              "defaultvalue": "*",
              "hint": "link for destination composition"
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
              "required": false,
              "defaultvalue": "",
              "hint": "Import layer syffix (usually identical to id)"
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "N",
              "hint": "Destination data scale measure",
              "setvalue": [
                {
                  "value": "N",
                  "label": "nominal"
                },
                {
                  "value": "O",
                  "label": "ordinal"
                },
                {
                  "value": "I",
                  "label": "interval"
                },
                {
                  "value": "R",
                  "label": "ratio"
                }
              ]
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
              "required": true,
              "defaultvalue": "",
              "hint": "Numerical value representing cell null"
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Cell type for raster data (vector denotes vector data, and text other types)",
              "setvalue": [
                {
                  "value": "Byte",
                  "label": "Unisgned 8 bit"
                }
              ]
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
              "required": true,
              "defaultvalue": "",
              "hint": "Data unit for raster cell data"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "parameters": {
        "rootprocid": "Ancillary",
        "subprocid": "anciltxttodb",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Register ancillary text data in db",
        "label": "Register locally organized ancillary text data in database"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "NA",
          "dstsystem": "ancillary",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "specimen",
          "srcsystem": "NA",
          "dstsystem": "specimen",
          "srcdivision": "NA",
          "dstdivision": "NA",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "template",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
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
              "defaultvalue": ""
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
              "defaultvalue": "txt"
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
            }
          ]
        },
        {
          "parent": "process",
          "element": "link",
          "parameter": [
            {
              "paramid": "csvcolumn",
              "paramtyp": "int",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "csvnodata",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "csvaltcolumn",
              "paramtyp": "int",
              "required": false,
              "defaultvalue": "-99"
            },
            {
              "paramid": "csvaltnodata",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "dbcolumn",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            }
          ]
        }
      ]
    }
  ]
}
```
