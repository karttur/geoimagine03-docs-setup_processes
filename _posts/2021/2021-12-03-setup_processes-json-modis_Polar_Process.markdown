---
layout: article
title: modis_Polar_Process_v090.json
categories: setup_processes
excerpt:  Install search, download and organize processes for NSIDC MODIS data holdings
tags:: 
    - json/modis_Polar_Process
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/modis Polar Process (setup_processes)

###  Install search, download and organize processes for NSIDC MODIS data holdings

The json command file <span class='file'>modis_Polar_Process_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "ModisPolar",
        "title": "Processes for MODIS data in EASE2 north grid projecion",
        "label": "Processes for MODIS data in EASE2 north grid projecion"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ModisPolar",
        "subprocid": "SearchModisPolarProducts",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Modis access available files in NSIDC holdings",
        "label": "Requires setup of wget and EarthData credentials file (called .netrc in user home path). Downloads the folder content as html."
      },
      "system": [
        {
          "system": "modispolar",
          "srcsystem": "modispolar",
          "dstsystem": "modispolar",
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
              "defaultvalue": "MYD10A2",
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
              "defaultvalue": "006",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
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
        "rootprocid": "ModisPolar",
        "subprocid": "ModisPolarSearchToDB",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Transfer the seanch results to the postgres DB",
        "label": "Transfer the seanch results to the postgres DB"
      },
      "system": [
        {
          "system": "modispolar",
          "srcsystem": "modispolar",
          "dstsystem": "modispolar",
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
              "defaultvalue": "MYD10A2",
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
              "defaultvalue": "006",
              "setvalue": [
                {
                  "value": "002",
                  "label": "002"
                }
              ]
            },
            {
              "paramid": "searchdone",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
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
        "rootprocid": "ModisPolar",
        "subprocid": "DownLoadModisPolar",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Download MODIS data from NSIDC",
        "label": "Download MODIS data from NSIDC"
      },
      "system": [
        {
          "system": "modispolar",
          "srcsystem": "modispolar",
          "dstsystem": "modispolar",
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
              "paramid": "searchdone",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
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
              "paramid": "downloaded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N"
            },
            {
              "paramid": "product",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "MYD10A2",
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
              "defaultvalue": "006",
              "setvalue": [
                {
                  "value": "006",
                  "label": "006"
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
        "rootprocid": "ModisPolar",
        "subprocid": "ExtractModisPolarHdf",
        "version": "0.9.0",
        "minuserstratum": "7",
        "title": "Extracts the content of modis NSIDC data>",
        "label": "Data must be organized prior to extration"
      },
      "system": [
        {
          "system": "modispolar",
          "srcsystem": "modispolar",
          "dstsystem": "modispolar",
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
              "defaultvalue": "hdf"
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
