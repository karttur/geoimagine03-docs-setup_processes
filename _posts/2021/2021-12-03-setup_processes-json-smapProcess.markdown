---
layout: article
title: smapProcess_v090.json
categories: setup_processes
excerpt:  Install SMAP specific processing
tags:: 
    - json/smapProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/smapProcess (setup_processes)

###  Install SMAP specific processing

The json command file <span class='file'>smapProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "SmapProc",
        "title": "Manage SMAP processes",
        "label": "Specific SMAP processes (order, download, organize)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SmapProc",
        "subprocid": "SearchSmapProducts",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Access available files in DAAC holding",
        "label": "Requires setup of wget and EarthData credentials file (called .netrc in user home path). Downloads the folder content as html."
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
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
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "SPL3SMP_E",
              "setvalue": [
                {
                  "value": "MCD43A4",
                  "label": "MCD43A4"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "002",
              "setvalue": [
                {
                  "value": "002",
                  "label": "002"
                }
              ]
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "https://n5eil01u.ecs.nsidc.org",
              "setvalue": [
                {
                  "value": "https://n5eil01u.ecs.nsidc.org",
                  "label": "https://n5eil01u.ecs.nsidc.org/"
                }
              ]
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
        "rootprocid": "SmapProc",
        "subprocid": "SmapSearchToDB",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Transfer the SMAP seanch results to the postgres DB",
        "label": "Open and reads html formatted files from searchDataPool"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
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
              "paramid": "remoteuser",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "SPL3SMP_E",
              "hint": "SMAP product to load",
              "setvalue": [
                {
                  "value": "SPL3SMP_E",
                  "label": "SPL3SMP_E"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006",
              "hint": "SMAP product version to load",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
                }
              ]
            },
            {
              "paramid": "searchdone",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "False"
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
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SmapProc",
        "subprocid": "DownLoadSmapDaac",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download SMAP data from DAAC",
        "label": "Download SMAP data from DAAC"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "remoteuser",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "serverurl",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "https://n5eil01u.ecs.nsidc.org",
              "setvalue": [
                {
                  "value": "https://n5eil01u.ecs.nsidc.org",
                  "label": "https://n5eil01u.ecs.nsidc.org/"
                }
              ]
            },
            {
              "paramid": "searchdone",
              "paramtyp": "Boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "SPL3SMP_E",
              "setvalue": [
                {
                  "value": "SPL3SMP_E",
                  "label": "SPL3SMP_E"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "002",
              "setvalue": [
                {
                  "value": "002",
                  "label": "002"
                }
              ]
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
              "defaultvalue": "hdf"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "hdf"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SmapProc",
        "subprocid": "ExtractSmapHdf",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Extracts the content of SMAP HDF>",
        "label": "Scenes must be organized prior to extration"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "asscript",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MYD29E1D",
              "setvalue": [
                {
                  "value": "MYD29E1D",
                  "label": "Sea ice 1D 4km EASE"
                },
                {
                  "value": "MOD29E1D",
                  "label": "Sea ice 1D 4km EASE"
                }
              ]
            },
            {
              "paramid": "version",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "006"
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
              "defaultvalue": "https://n5eil01u.ecs.nsidc.org",
              "setvalue": [
                {
                  "value": "https://n5eil01u.ecs.nsidc.org",
                  "label": "https://n5eil01u.ecs.nsidc.org/"
                }
              ]
            },
            {
              "paramid": "searchdone",
              "paramtyp": "Boolean",
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
              "defaultvalue": ""
            },
            {
              "paramid": "hdr",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "h5"
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
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SmapProc",
        "subprocid": "CheckSMAP",
        "version": "0.8.0",
        "minuserstratum": 7,
        "title": "Check SMAP download and extraction>",
        "label": "Check SMAP download and extraction"
      },
      "system": [
        {
          "system": "smap",
          "srcsystem": "smap",
          "dstsystem": "smap",
          "srcdivision": "region",
          "dstdivision": "region",
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
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "setvalue": [
                {
                  "value": "SPL3SMP_E",
                  "label": "SPL3SMP_E"
                }
              ]
            },
            {
              "paramid": "version",
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
              "defaultvalue": "h5"
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
        }
      ]
    }
  ]
}
```
