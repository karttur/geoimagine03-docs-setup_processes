---
layout: article
title: manage_project_v090.json
categories: setup_processes
excerpt:  Install project management processes
tags:: 
    - json/manage_project
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/manage project (setup_processes)

###  Install project management processes

The json command file <span class='file'>manage_project_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "overwrite": false,
      "processid": "addrootproc",
      "parameters": {
        "rootprocid": "ManageProject",
        "title": "Manage projects",
        "label": "Add, update, construct or delete projects"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageProject",
        "subprocid": "ManageDefRegProj",
        "version": "0.9.0",
        "minuserstratum": 4,
        "title": "Create project",
        "label": "Create a project and a default project tract based on a default region"
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
              "paramid": "defaultregion",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Select a default region"
            },
            {
              "paramid": "tractid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Set a unique tractid"
            },
            {
              "paramid": "tractname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Tract name"
            },
            {
              "paramid": "tracttitle",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Give a title for the tract (for maps)"
            },
            {
              "paramid": "tractlabel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a label for the tract"
            },
            {
              "paramid": "projid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Project id (can be the same as the tractid)"
            },
            {
              "paramid": "projname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Project name"
            },
            {
              "paramid": "projtitle",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a title for the project"
            },
            {
              "paramid": "projlabel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a label for the project"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageProject",
        "subprocid": "ManageTractProj",
        "version": "0.9.0",
        "minuserstratum": 4,
        "title": "Create project from tract",
        "label": "Create a new project from an existing user tract"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "region",
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
              "paramid": "tractid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Select an existing tractid"
            },
            {
              "paramid": "projid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "",
              "hint": "Project id (can be the same as the tractid)"
            },
            {
              "paramid": "projtitle",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a title for the project"
            },
            {
              "paramid": "projlabel",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "",
              "hint": "Give a label for the project"
            },
            {
              "paramid": "modtilelink",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "MODIS project link"
            },
            {
              "paramid": "wrstilelink",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Landsat WRS project link"
            },
            {
              "paramid": "mgrstilelink",
              "paramtyp": "boolean",
              "required": false,
              "defaultvalue": false,
              "hint": "Sentinel MGRS project link"
            }
          ]
        }
      ]
    }
  ]
}
```
