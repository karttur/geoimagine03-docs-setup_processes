---
layout: article
title: sentinelProcess_v090.json
categories: setup_processes
excerpt:  Install specific processes for sentinel data
tags:: 
    - json/sentinelProcess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/sentinelProcess (setup_processes)

###  Install specific processes for sentinel data

The json command file <span class='file'>sentinelProcess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "SentinelProcess",
        "title": "Manage Sentinel processes",
        "label": "Specific Sentinel processes (download, organise, explode, cloud, masking)"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "DownloadSentinelAncillary",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download Sentinel granule meta data",
        "label": "Download Sentinel granule meta data using vectors"
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
        }
      ],
      "nodes": [
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "tablesearchid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "searchid"
            },
            {
              "paramid": "granuleoverlap",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.1"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "30"
            },
            {
              "paramid": "startdate",
              "paramtyp": "date",
              "required": true,
              "defaultvalue": "20140401"
            },
            {
              "paramid": "enddate",
              "paramtyp": "date",
              "required": true,
              "defaultvalue": "20180821"
            },
            {
              "paramid": "startdoy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "1"
            },
            {
              "paramid": "enddoy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "365"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
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
              "required": true,
              "defaultvalue": "*"
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
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "DownloadSentinelRegion",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download Sentinel granule meta data",
        "label": "Download Sentinel granule meta data using region"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "system",
          "dstsystem": "sentinel",
          "srcdivision": "region",
          "dstdivision": "tiles",
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
              "paramid": "copycomp",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "systemregion"
            },
            {
              "paramid": "tablesearchid",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "regionid"
            },
            {
              "paramid": "granuleoverlap",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0.1"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "30"
            },
            {
              "paramid": "startdate",
              "paramtyp": "date",
              "required": true,
              "defaultvalue": "20140401"
            },
            {
              "paramid": "enddate",
              "paramtyp": "date",
              "required": true,
              "defaultvalue": "20300101"
            },
            {
              "paramid": "startdoy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "1"
            },
            {
              "paramid": "enddoy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "365"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
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
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "DownloadSentinelData",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download Sentinel data",
        "label": "Download Sentinel data from entrieds in db"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "region",
          "dstdivision": "tiles",
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
              "paramid": "tiles",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "downloaded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "setvalue": [
                {
                  "value": "N",
                  "label": "No (download only tiles not registered as downloaded)"
                },
                {
                  "value": "Y",
                  "label": "Yes (download only tiles registered as downloaded)"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "30"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "DownloadSentinelDataRegion",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download Sentinel data",
        "label": "Download Sentinel data from entries in db"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "system",
          "dstsystem": "sentinel",
          "srcdivision": "region",
          "dstdivision": "tiles",
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
              "paramid": "tiles",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "downloaded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "setvalue": [
                {
                  "value": "N",
                  "label": "No (download only tiles not registered as downloaded)"
                },
                {
                  "value": "Y",
                  "label": "Yes (download only tiles registered as downloaded)"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "30"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "DownloadSentinelTile",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Download Sentinel data",
        "label": "Download Sentinel data from entrieds in db"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
              "paramid": "tileid",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": "tileid"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "downloaded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "setvalue": [
                {
                  "value": "N",
                  "label": "No (download only tiles not registered as downloaded)"
                },
                {
                  "value": "Y",
                  "label": "Yes (download only tiles registered as downloaded)"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "30"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "FindGranuleTiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Find mgrs tiles covered by granulue",
        "label": "Find mgrs tiles covered by granulue"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
              "paramid": "granuleoverlap",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": "0.1"
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "downloaded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "setvalue": [
                {
                  "value": "N",
                  "label": "No (download only tiles not registered as downloaded)"
                },
                {
                  "value": "Y",
                  "label": "Yes (download only tiles registered as downloaded)"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "GRD",
              "setvalue": [
                {
                  "value": "GRD",
                  "label": "GRD"
                }
              ]
            },
            {
              "paramid": "mgrsversion",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "NGA",
              "setvalue": [
                {
                  "value": "NGA",
                  "label": "NGA"
                },
                {
                  "value": "ESA",
                  "label": "ESA"
                },
                {
                  "value": "NGAESA",
                  "label": "NGAESA"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "100"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "ExplodeSentinel",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Explode Sentinel tiles",
        "label": "Explode Sentinel tiles from entried in db"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
              "paramid": "granuleoverlap",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": "0.1"
            },
            {
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "exploded",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "N",
              "setvalue": [
                {
                  "value": "N",
                  "label": "No (download only tiles not registered as downloaded)"
                },
                {
                  "value": "Y",
                  "label": "Yes (download only tiles registered as downloaded)"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                },
                {
                  "value": "GRD",
                  "label": "GRD"
                }
              ]
            },
            {
              "paramid": "cloudmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "setcloudmask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "setdetfoomask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "setnodatamask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "setdefectask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "setsaturamask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "settecquamask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "set0tonull",
              "paramtyp": "boolean",
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
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
              "defaultvalue": "tif"
            }
          ]
        }
      ]
    },
  
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "GeoCheckSentinelTiles",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Check geolocation of sentinel tile",
        "label": "Must first check MSI data and set mgrs to allow SAR-C data to be organized"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "tiles",
          "dstdivision": "tiles",
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
              "paramid": "orbitdirection",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "B",
              "setvalue": [
                {
                  "value": "B",
                  "label": "Both"
                },
                {
                  "value": "A",
                  "label": "Ascending"
                },
                {
                  "value": "D",
                  "label": "Descending"
                }
              ]
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
                }
              ]
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
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "tif"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "SentinelProcess",
        "subprocid": "ReorganiseSentinel",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Reorganize Sentinel tiles and granules",
        "label": "Reorganize Sentinel tiles and granules"
      },
      "system": [
        {
          "system": "sentinel",
          "srcsystem": "sentinel",
          "dstsystem": "sentinel",
          "srcdivision": "region",
          "dstdivision": "tiles",
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
              "paramid": "searchpath",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "tiles",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "platformname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "Sentinel-2",
              "setvalue": [
                {
                  "value": "Sentinel-1",
                  "label": "Sentinel-1"
                },
                {
                  "value": "Sentinel-2",
                  "label": "Sentinel-2"
                },
                {
                  "value": "Sentinel-3",
                  "label": "Sentinel-3"
                }
              ]
            },
            {
              "paramid": "prodtype",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "S2MSI1C",
              "setvalue": [
                {
                  "value": "S2MSI1C",
                  "label": "S2MSI1C"
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
              "defaultvalue": "zip"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "zip"
            }
          ]
        }
      ]
    }
  ]
}
```
