---
layout: article
title: regions_Tract+Site_FromVector_v090.json
categories: setup_processes
excerpt:  Install sub process TractFromVector & SiteFromVector
tags:: 
    - json/regions_Tract+Site_FromVector
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions Tract+Site FromVector (setup_processes)

###  Install sub process TractFromVector & SiteFromVector

The json command file <span class='file'>regions_Tract+Site_FromVector_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "subprocid": "TractFromVector",
        "version": "0.9.0",
        "minuserstratum": 3,
        "title": "Define tract from extent",
        "label": "Automatically define tract from extent of vector data set"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "region",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "modis",
          "srcsystem": "NA",
          "dstsystem": "modis",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2T",
          "srcsystem": "NA",
          "dstsystem": "ease2T",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6933
        },
        {
          "system": "ease2N",
          "srcsystem": "NA",
          "dstsystem": "ease2N",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2S",
          "srcsystem": "NA",
          "dstsystem": "ease2S",
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
              "paramid": "defaultregion",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Select a default region to use for defining your tract"
            },
            {
              "paramid": "tractid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Set a unique tractid"
            },
            {
              "paramid": "tracttitle",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Give a title for the new tract (for maps)"
            },
            {
              "paramid": "tractlabel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a label for the tract"
            },
            {
              "paramid": "buffer",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "Buffer in map units to expand region comapred to data points"
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
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "srctractextent",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "",
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
              "defaultvalue": "process",
              "hint": "Default hierarchical child name"
            }
          ]
        },
        {
          "parent": "srccomp",
          "element": "srctractextent",
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
              "defaultvalue": "srctractextent",
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
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "SiteFromVector",
        "version": "0.9.0",
        "minuserstratum": 3,
        "title": "Define site from extent",
        "label": "Automatically define site from extent of vector data set"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "region",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 4326
        },
        {
          "system": "modis",
          "srcsystem": "NA",
          "dstsystem": "modis",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6842
        },
        {
          "system": "ease2T",
          "srcsystem": "NA",
          "dstsystem": "ease2T",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6933
        },
        {
          "system": "ease2N",
          "srcsystem": "NA",
          "dstsystem": "ease2N",
          "srcdivision": "NA",
          "dstdivision": "region",
          "srcepsg": 0,
          "dstepsg": 6931
        },
        {
          "system": "ease2S",
          "srcsystem": "NA",
          "dstsystem": "ease2S",
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
              "paramid": "tractid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Select a tract to use for defining your site"
            },
            {
              "paramid": "siteid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Set a unique siteid"
            },
            {
              "paramid": "sitetitle",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Give a title for the new site (for maps)"
            },
            {
              "paramid": "sitelabel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a label for the site"
            },
            {
              "paramid": "buffer",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0,
              "hint": "Buffer in map units to expand site comapred to data points"
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
          "element": "srccomp",
          "parameter": [
            {
              "paramid": "srcsiteextent",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": "",
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
              "defaultvalue": "process",
              "hint": "Default hierarchical child name"
            }
          ]
        },
        {
          "parent": "srccomp",
          "element": "srcsiteextent",
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
              "defaultvalue": "srcsiteextent",
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
        }
      ]
    }
  ]
}
```
