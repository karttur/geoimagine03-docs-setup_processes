---
layout: article
title: ExportZip_v090.json
categories: setup_processes
excerpt:  Install export processes for Zip backup
tags:: 
    - json/ExportZip
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/ExportZip (setup_processes)

###  Install export processes for Zip backup

The json command file <span class='file'>ExportZip_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "parameters": {
        "rootprocid": "Export",
        "title": "Export spatial data",
        "label": "Export spatial data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ZipArchiveRegion",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Export zip compressed data",
        "label": "Export data while compressing to defined zip format"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "export",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 0
        },
        {
          "system": "modis",
          "srcsystem": "modis",
          "dstsystem": "export",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6842,
          "dstepsg": 0
        },
        {
          "system": "ease2n",
          "srcsystem": "ease2n",
          "dstsystem": "export",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6931,
          "dstepsg": 6931
        },
        {
          "system": "ease2s",
          "srcsystem": "ease2s",
          "dstsystem": "export",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 6932,
          "dstepsg": 0
        },
        {
          "system": "ease2t",
          "srcsystem": "ease2t",
          "dstsystem": "export",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "zip",
              "paramtyp": "text",
              "tagorattr": "Attr",
              "required": "N",
              "defaultvalue": "gzip"
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
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ZipArchiveTiles",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Export zip compressed data",
        "label": "Export data while compressing to defined zip format"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "export",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
          "srcepsg": 0,
          "dstepsg": 0
        },
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
              "defaultvalue": "tar.gz"
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
    }
  ]
}
```
