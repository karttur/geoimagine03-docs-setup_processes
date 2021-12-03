---
layout: article
title: regions-root+categories_v090.json
categories: setup_processes
excerpt:  Install region root and categories processes
tags:: 
    - json/regions-root+categories
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/regions root+categories (setup_processes)

###  Install region root and categories processes

The json command file <span class='file'>regions-root+categories_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "ManageRegion",
        "title": "Manage regions for bulk processing",
        "label": "Create, change or delete regions"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageRegion",
        "subprocid": "RegionCategories",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Define default region categories for public use",
        "label": "Only superuser can set region categories, send request it you really need a new region category"
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
              "paramid": "regioncat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Region category"
            },
            {
              "paramid": "parentcat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Region parent category"
            },
            {
              "paramid": "stratum",
              "paramtyp": "integer",
              "required": true,
              "defaultvalue": "0",
              "hint": "Minimum stratum for access",
              "minmax": {
                "min": 0,
                "max": 100
              }
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Region category title"
            },
            {
              "paramid": "label",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Region category label"
            }
          ]
        }
      ]
    }
  ]
}
```
