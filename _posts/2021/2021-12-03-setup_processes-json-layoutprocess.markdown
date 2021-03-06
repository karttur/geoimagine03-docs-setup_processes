---
layout: article
title: layoutprocess_v090.json
categories: setup_processes
excerpt:  Installs processes for map layout
tags:: 
    - json/layoutprocess
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/layoutprocess (setup_processes)

###  Installs processes for map layout

The json command file <span class='file'>layoutprocess_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

```
{
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
      "processid": "addrootproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "LayoutProc",
        "title": "Manage Layout processes",
        "label": "Manage Layout processes"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "LayoutProc",
        "subprocid": "AddRasterPalette",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Add raster palette",
        "label": "Add raster palette"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "palette",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "compid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "access",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "A"
            },
            {
              "paramid": "default",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            }
          ]
        },
        {
          "parent": "process",
          "element": "parameters",
          "parameter": [
            {
              "paramid": "setcolor",
              "paramtyp": "element",
              "required": true,
              "defaultvalue": ""
            }
          ]
        },
        {
          "parent": "parameters",
          "element": "setcolor",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "red",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "green",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "blue",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "alpha",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "label",
              "paramtyp": "string",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "hint",
              "paramtyp": "string",
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
        "rootprocid": "LayoutProc",
        "subprocid": "CreateLegend",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Create legend for raster layer",
        "label": "Create legend for raster layer"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "palmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 250
            },
            {
              "paramid": "palmin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "two51",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "two52",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "two53",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "two54",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "two55",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "height",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 500
            },
            {
              "paramid": "width",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 100
            },
            {
              "paramid": "soloheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 70
            },
            {
              "paramid": "pngwidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300
            },
            {
              "paramid": "pngheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "A"
            },
            {
              "paramid": "buffer",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{10,10,10,10}"
            },
            {
              "paramid": "margin",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{10,5,10,5}"
            },
            {
              "paramid": "textpadding",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{10,5,10,5}"
            },
            {
              "paramid": "framecolor",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 254
            },
            {
              "paramid": "framefill",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "framestrokewidth",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "1.0"
            },
            {
              "paramid": "label",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "fontcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "font",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Verdana"
            },
            {
              "paramid": "fontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12
            },
            {
              "paramid": "fonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "titlefontcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "titlefont",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Verdana"
            },
            {
              "paramid": "titlefontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 16
            },
            {
              "paramid": "titlefonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "sticklen",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "compresslabels",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "separatebuffer",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{5,5,5,5}"
            },
            {
              "paramid": "precision",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "columnhead",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "columns",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "matrix",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "columntext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "rowtext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "rowhead",
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
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "LayoutProc",
        "subprocid": "AddMovieClock",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Add movieclock layout",
        "label": "Add movieclock layout"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "name",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "tlmargin",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{5,5,5,5}"
            },
            {
              "paramid": "clmargin",
              "paramtyp": "string",
              "required": false,
              "defaultvalue": "{5,5,5,5}"
            },
            {
              "paramid": "position",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "ll"
            },
            {
              "paramid": "bgcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "tlborder",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2
            },
            {
              "paramid": "clborder",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 6
            },
            {
              "paramid": "tlbordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "beige"
            },
            {
              "paramid": "clbordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "beige"
            },
            {
              "paramid": "clcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "blue"
            },
            {
              "paramid": "tlheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "tlticks",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "tltickwidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2
            },
            {
              "paramid": "tickcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "beige"
            },
            {
              "paramid": "boettcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "silver"
            },
            {
              "paramid": "textatclock",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "tlcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "purple"
            },
            {
              "paramid": "clradius",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 50
            },
            {
              "paramid": "clhandcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "purple"
            },
            {
              "paramid": "clframecolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "fontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 24
            },
            {
              "paramid": "fontcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "grey"
            },
            {
              "paramid": "fontbackground",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "rotate",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "font",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Arial"
            },
            {
              "paramid": "textinvideo",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "transparent",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "LayoutProc",
        "subprocid": "MovieClock",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Create movieclock layout",
        "label": "Create movieclock layout"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "width",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 900
            },
            {
              "paramid": "name",
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
        "rootprocid": "LayoutProc",
        "subprocid": "CreateScaling",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Create legend for raster layer",
        "label": "Create legend for raster layer"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "log",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "power",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "powerna",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 251
            },
            {
              "paramid": "mirror0",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "scalefac",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "1"
            },
            {
              "paramid": "offsetadd",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "srcmin",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "srcmax",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "dstmin",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "dstmax",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            }
          ]
        },
        {
          "parent": "process",
          "element": "comp",
          "parameter": [
            {
              "paramid": "id",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
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
              "defaultvalue": ""
            },
            {
              "paramid": "suffix",
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
        "rootprocid": "LayoutProc",
        "subprocid": "ExportLegend",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Export legend for raster layer",
        "label": "Export legend for raster layer"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "palette",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "legendnominal",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "legendbackground",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "White"
            },
            {
              "paramid": "legendopacity",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0,
              "Hint": "0 for transparent 255 for opacity"
            },
            {
              "paramid": "legendpalmax",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 250
            },
            {
              "paramid": "legendpalmin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "legendtwo51",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendtwo52",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendtwo53",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendtwo54",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendtwo55",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 500
            },
            {
              "paramid": "legendwidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 100
            },
            {
              "paramid": "legendsoloheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 70
            },
            {
              "paramid": "legendpngwidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300
            },
            {
              "paramid": "legendpngheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 300
            },
            {
              "paramid": "measure",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "A"
            },
            {
              "paramid": "legendbuffer",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendmargin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendtextpadding",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendframecolor",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 254
            },
            {
              "paramid": "legendframefill",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "legendframestrokewidth",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "1.0"
            },
            {
              "paramid": "legendlabel",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "legendfontcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "legendfont",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Verdana"
            },
            {
              "paramid": "legendfontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12
            },
            {
              "paramid": "legendfonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "legendtitlefontcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "legendtitlefont",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "Verdana"
            },
            {
              "paramid": "legendtitlefontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12
            },
            {
              "paramid": "legendtitlefonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "legendsticklen",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendcompresslabels",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendseparatebuffer",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendcolumnhead",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "legendcolumns",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "legendmatrix",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendcolumntext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "legendrowtext",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "legendrowhead",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "jpg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
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
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "LayoutProc",
        "subprocid": "AddPubText",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Add raster palette",
        "label": "Add raster palette"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "compid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "palversion",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "product",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "suffix",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "title",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "header",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "subheader",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "legendheader",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "legendtype",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "banner",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "hints",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "acknow",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "descript",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "reference",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "disclaim",
              "paramtyp": "string",
              "tagorattr": "Tag",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "copyrigth",
              "paramtyp": "string",
              "tagorattr": "Tag",
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
        "rootprocid": "LayoutProc",
        "subprocid": "UpdateRasterMeta",
        "version": "0.8.0",
        "minuserstratum": 10,
        "title": "Replace null and color ramp in existing raster"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "cellnull",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "celltype",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "scalefac",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "offsetadd",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "dataunit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
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
          "element": "dstpath",
          "parameter": [
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
              "defaultvalue": "src"
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
        }
      ]
    }
  ]
}
```
