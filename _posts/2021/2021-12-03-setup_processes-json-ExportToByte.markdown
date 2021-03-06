---
layout: article
title: ExportToByte_v090.json
categories: setup_processes
excerpt:  Install processes for exporting data as color byte binary images
tags:: 
    - json/ExportToByte
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/ExportToByte (setup_processes)

###  Install processes for exporting data as color byte binary images

The json command file <span class='file'>ExportToByte_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "title": "Export spatial data",
        "label": "Export spatial data"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportTilesToByte",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Export tiles to byte binary",
        "label": "Export  tiles to byte binary with color coding"
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
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default"
            },
            {
              "paramid": "minmax",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "srcmin",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "srcmax",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "zscore",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "globalmeantozero",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "globalmean",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "globalstd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "zscorefac",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "dynamicmask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "masknotnullin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 255
            },
            {
              "paramid": "vectoroverlay",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "width",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "crop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "border",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "bordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "emboss",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "embossdims",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "embossptsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "titlesingleline",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "titlegravity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "North"
            },
            {
              "paramid": "titlebackgroundcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "white",
              "hint": "Any color code accpeted by ImageMagick"
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
              "defaultvalue": "Tahoma"
            },
            {
              "paramid": "titlefontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12
            },
            {
              "paramid": "detailcrop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "detailwidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "detailborder",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2
            },
            {
              "paramid": "detailbordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "detailtitle",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": true
            },
            {
              "paramid": "detaillegend",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "detaillegendgravity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "East"
            },
            {
              "paramid": "detaillegendsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 100
            },
            {
              "paramid": "detaillegendbackground",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "White"
            },
            {
              "paramid": "jpg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportShadedTilesToByte",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Export tiles to byte binary",
        "label": "Export  tiles to byte binary with color coding"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default"
            },
            {
              "paramid": "alphashade",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "fuzzalpha",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "shadefactor",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 2,
              "hint": "1, 2, 4, 8 etc; higher = darker"
            },
            {
              "paramid": "bumpshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "minmax",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "srcmin",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "srcmax",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "zscore",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "globalmeantozero",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "globalmean",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "globalstd",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "zscorefac",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "dynamicmask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "masknotnullin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 255
            },
            {
              "paramid": "vectoroverlay",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "width",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "crop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "border",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "bordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "emboss",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "embossdims",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "embossptsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "titlesingleline",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "titlegravity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "North"
            },
            {
              "paramid": "titlebackgroundcolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "white",
              "hint": "Any color code accpeted by ImageMagick"
            },
            {
              "paramid": "titlebackgroundalpha",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": "0.5",
              "hint": "Title background transparency"
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
              "defaultvalue": "Tahoma"
            },
            {
              "paramid": "titlefontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 12
            },
            {
              "paramid": "jpg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "detaillegend",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "detaillegendgravity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "East"
            },
            {
              "paramid": "detaillegendsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 100
            },
            {
              "paramid": "detaillegendbackground",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "White"
            },
            {
              "paramid": "jpg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportTilesToMap",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Export tiles to map",
        "label": "Export tiles to map"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "palette",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default"
            },
            {
              "paramid": "dynamicmask",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "masknotnullin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 255
            },
            {
              "paramid": "vectoroverlay",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "width",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "crop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "border",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "bordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "emboss",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "embossdims",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "embossptsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
            {
              "paramid": "jpg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "0"
            },
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
              "paramid": "plotwidth",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 8
            },
            {
              "paramid": "plotheight",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 6
            },
            {
              "paramid": "buffer",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "margin",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "textpadding",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "legendposition",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "right"
            },
            {
              "paramid": "legendfitaxis",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "legendrelativesize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "5"
            },
            {
              "paramid": "legendpad",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "legendborderpad",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 1.5
            },
            {
              "paramid": "legendinsetaxis",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": "False"
            },
            {
              "paramid": "legendinsetposition",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 3
            },
            {
              "paramid": "legendrelativewidth",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 5
            },
            {
              "paramid": "legendrelativeheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 35
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
              "paramid": "soloheight",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 70
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
              "defaultvalue": 1
            },
            {
              "paramid": "legendticks",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
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
              "defaultvalue": ""
            },
            {
              "paramid": "legendfontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "legendfonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "titleypos",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 1.08
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
              "defaultvalue": ""
            },
            {
              "paramid": "titlefontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "titlefonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "axisfontcolors",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black,black"
            },
            {
              "paramid": "axisfont",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "axisfontsize",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "axisfonteffect",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "majorticks",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "minorticks",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "majortickdirection",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "inout"
            },
            {
              "paramid": "majorticklength",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 6
            },
            {
              "paramid": "majortickwidth",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "majortickcolors",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black,black"
            },
            {
              "paramid": "minortickdirection",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "in"
            },
            {
              "paramid": "minorticklength",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 2
            },
            {
              "paramid": "minortickwidth",
              "paramtyp": "float",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "minortickcolors",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "gray,gray"
            },
            {
              "paramid": "gridcolors",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "gray,gray"
            },
            {
              "paramid": "gridlinestyle",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "--"
            },
            {
              "paramid": "gridlinewidth",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "gridalpha",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "spinecolors",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black,black,black,black"
            },
            {
              "paramid": "spinelinestyle",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "-"
            },
            {
              "paramid": "spinelinewidth",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "spinepattern",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "spinexlabels",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "spineylabels",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "northarrow",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "northarrowsize",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0.5
            },
            {
              "paramid": "northarrowanchor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "upperleft"
            },
            {
              "paramid": "northarrowmarginx",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 5
            },
            {
              "paramid": "northarrowmarginy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 5
            },
            {
              "paramid": "northarrowx",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "northarrowy",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "logo",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "kartturnorth01"
            },
            {
              "paramid": "logopos",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "upperleft"
            },
            {
              "paramid": "logox",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "logoy",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "separatebuffer",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 10
            },
            {
              "paramid": "columnhead",
              "paramtyp": "text",
              "required": false,
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
            },
            {
              "paramid": "tightlayout",
              "paramtyp": "boolean",
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
              "defaultvalue": "png"
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportTilesToSvg",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Export data to SVG",
        "label": "Export data to SVG color coding"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "tolerance",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "simplify",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "scale",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "dstepsg",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": "4326"
            },
            {
              "paramid": "stroke",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "fill",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "none"
            },
            {
              "paramid": "symbol",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "strokewidth",
              "paramtyp": "real",
              "required": false,
              "defaultvalue": 1
            },
            {
              "paramid": "strokedasharray",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "padding",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "pngsize",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "crop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "asscript",
              "paramtyp": "boolean",
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
              "defaultvalue": "svg"
            },
            {
              "paramid": "dat",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "png"
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportsToMovieFrames",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Convert exported images to movie frames",
        "label": "Convert exported images to movie frames"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "name",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default"
            },
            {
              "paramid": "width",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "crop",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": ""
            },
            {
              "paramid": "border",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "bordercolor",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "black"
            },
            {
              "paramid": "emboss",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "KARTTUR"
            },
            {
              "paramid": "embossdims",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "embossptsize",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "asscript",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "vectoroverlay",
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportMovieClockLayout",
        "version": "0.8.0",
        "minuserstratum": "10",
        "title": "Create movieclock layout",
        "label": "Create movieclock layout"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
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
            },
            {
              "paramid": "asscript",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "vector",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "NA"
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
              "defaultvalue": "png"
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
      "delete": false,
      "parameters": {
        "rootprocid": "Export",
        "subprocid": "ExportMovieOverlayFrames",
        "version": "0.9.0",
        "minuserstratum": "10",
        "title": "Convert 2 sets of exported images to movie frames with baselayer and overlayer",
        "label": "Convert 2 sets of exported images to movie frames with baselayer and overlayer"
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
              "paramid": "overwriteshade",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "overwritelayout",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false
            },
            {
              "paramid": "name",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "default"
            },
            {
              "paramid": "basewidth",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "basecrop",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "overlaywidth",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "gravity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "northeast"
            },
            {
              "paramid": "geomx",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "geomy",
              "paramtyp": "integer",
              "required": false,
              "defaultvalue": 0
            },
            {
              "paramid": "emboss",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "KARTTUR"
            },
            {
              "paramid": "embossdims",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": ""
            },
            {
              "paramid": "embossptsize",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": 0
            },
            {
              "paramid": "asscript",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "True"
            },
            {
              "paramid": "vector",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "NA"
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
          "element": "base",
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
          "parent": "srccomp",
          "element": "overlay",
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
