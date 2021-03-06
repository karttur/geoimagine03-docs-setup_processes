---
layout: article
title: reproject_systemregion_process_v090.json
categories: setup_processes
excerpt:  Install processes for reproject between projection systems
tags:: 
    - json/reproject_systemregion_process
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/reproject systemregion process (setup_processes)

###  Install processes for reproject between projection systems

The json command file <span class='file'>reproject_systemregion_process_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "Reproject",
        "title": "Reproject layer from one system to another",
        "label": "Reproject layer from one system to another"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "Reproject",
        "subprocid": "ReprojectAncillaryRegion",
        "version": "0.9.0",
        "minuserstratum": 5,
        "title": "Reproject ancillary regional data"
      },
      "system": [
        {
          "system": "modis",
          "srcsystem": "ancillary",
          "dstsystem": "modis",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "landsat",
          "srcsystem": "ancillary",
          "dstsystem": "landsat",
          "srcdivision": "region",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 3200
        },
        {
          "system": "ease2n",
          "srcsystem": "ancillary",
          "dstsystem": "ease2n",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "1.3"
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "defregid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "The default region id of the source region to tile must be given"
            },
            {
              "paramid": "tr_xres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "tr_yres",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
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
            }
            ,
            {
              "paramid": "errorthreshold",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0,
              "hint": "error threshold for transformer (in pixels) 0 = auto"
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
