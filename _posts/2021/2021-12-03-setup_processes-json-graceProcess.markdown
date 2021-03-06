---
layout: article
title: graceProcess_v090.json
categories: setup_processes
excerpt:  Install GRACE specific processing
tags:: 
    - json/graceProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/graceProcess (setup_processes)

###  Install GRACE specific processing

The json command file <span class='file'>graceProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "GraceProc",
        "title": "Grace data processing",
        "label": "Processes for downloading and organizing grace data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "GraceProc",
        "subprocid": "SearchGraceProducts",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Access available files in po-DAAC holding",
        "label": "Requires setup of wget and EarthData credentials file (called .netrc in user home path). Downloads the folder content as html."
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "none",
          "dstdivision": "none",
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
              "paramid": "feature",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "land_mass",
              "setvalue": [
                {
                  "value": "land_mass",
                  "label": "land_mass"
                }
              ]
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "RL06",
              "setvalue": [
                {
                  "value": "RL06",
                  "label": "RL06"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v03",
              "setvalue": [
                {
                  "value": "v03",
                  "label": "v03"
                }
              ]
            },
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "JPL",
              "setvalue": [
                {
                  "value": "CSR",
                  "label": "CSR"
                },
                {
                  "value": "GFZ",
                  "label": "GFZ"
                },
                {
                  "value": "JPL",
                  "label": "JPL"
                }
              ]
            },
            {
              "paramid": "remoteuser",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": true,
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
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "GraceProc",
        "subprocid": "CurlGrace",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Curl Grace data via html coded url",
        "label": "Curl Grace data via html coded url"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "none",
          "dstdivision": "none",
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
              "paramid": "feature",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "land_mass",
              "setvalue": [
                {
                  "value": "land_mass",
                  "label": "land_mass"
                }
              ]
            },
            {
              "paramid": "content",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "RL06",
              "setvalue": [
                {
                  "value": "RL06",
                  "label": "RL06"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v03",
              "setvalue": [
                {
                  "value": "v03",
                  "label": "v03"
                }
              ]
            },
            {
              "paramid": "source",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "JPL",
              "setvalue": [
                {
                  "value": "CSR",
                  "label": "CSR"
                },
                {
                  "value": "GFZ",
                  "label": "GFZ"
                },
                {
                  "value": "JPL",
                  "label": "JPL"
                }
              ]
            },
            {
              "paramid": "remoteuser",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "serverurl",
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
              "required": false,
              "defaultvalue": "tif"
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
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "GraceProc",
        "subprocid": "OrganizeGrace",
        "version": "0.9.0",
        "minuserstratum": 1,
        "title": "Organize grace data",
        "label": "Organize local (downloaded or created) grace data"
      },
      "system": [
        {
          "system": "ancillary",
          "srcsystem": "ancillary",
          "dstsystem": "ancillary",
          "srcdivision": "none",
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
              "paramid": "feature",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "land_mass",
              "setvalue": [
                {
                  "value": "land_mass",
                  "label": "land_mass"
                }
              ]
            },
            {
              "paramid": "model",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "RL06",
              "setvalue": [
                {
                  "value": "RL06",
                  "label": "RL06"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "v03",
              "setvalue": [
                {
                  "value": "v03",
                  "label": "v03"
                }
              ]
            },
            {
              "paramid": "solutionset",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "JPL",
              "setvalue": [
                {
                  "value": "CSR",
                  "label": "CSR"
                },
                {
                  "value": "GFZ",
                  "label": "GFZ"
                },
                {
                  "value": "JPL",
                  "label": "JPL"
                }
              ]
            },
            {
              "paramid": "accessdate",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Date of accessing dataset (if left blank todays date will be recorded)"
            },
            {
              "paramid": "dataurl",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "url for source dataset"
            },
            {
              "paramid": "metaurl",
              "paramtyp": "text",
              "required": true,
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
              "paramid": "cellnull",
              "paramtyp": "float",
              "required": false,
              "defaultvalue":-99999.0,
              "hint": "cellnull for GRACE data to organize"
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
              "defaultvalue": "tif",
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
