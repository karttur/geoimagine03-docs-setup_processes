---
layout: article
title: manageuser_v090.json
categories: setup_processes
excerpt:  Install user management processes
tags:: 
    - json/manageuser
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/manageuser (setup_processes)

###  Install user management processes

The json command file <span class='file'>manageuser_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "ManageUser",
        "title": "Manage Users",
        "label": "Add, update or remover users"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "ManageUser",
        "subprocid": "ManageUser",
        "version": "0.9.0",
        "minuserstratum": 9,
        "title": "Add, update or remover users",
        "label": "Add, update or remover users"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "NA",
          "dstsystem": "NA",
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
              "paramid": "userid",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "''",
              "hint": "User id"
            },
            {
              "paramid": "userpswd",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "''",
              "hint": "User pass word"
            },
            {
              "paramid": "usercat",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "''",
              "hint": "user category",
              "setvalue": [
                {
                  "value": "viewer",
                  "label": "view user"
                },
                {
                  "value": "viewergroup",
                  "label": "viewer user group"
                },
                {
                  "value": "tract",
                  "label": "single tract user"
                },
                {
                  "value": "tractgroup",
                  "label": "single tract user group"
                },
                {
                  "value": "state",
                  "label": "state specific user"
                },
                {
                  "value": "stategroup",
                  "label": "state specific user group"
                },
                {
                  "value": "country",
                  "label": "country specific user"
                },
                {
                  "value": "countrygroup",
                  "label": "country specific user group"
                },
                {
                  "value": "continent",
                  "label": "continent specific user"
                },
                {
                  "value": "global",
                  "label": "global user"
                },
                {
                  "value": "globalgroup",
                  "label": "global user group"
                },
                {
                  "value": "develop",
                  "label": "development user"
                },
                {
                  "value": "developgroup",
                  "label": "development user group"
                },
                {
                  "value": "science",
                  "label": "scientific user"
                },
                {
                  "value": "sciencegroup",
                  "label": "scientific user group"
                },
                {
                  "value": "sciencegroup",
                  "label": "scientific user group"
                },
                {
                  "value": "super",
                  "label": "global super user"
                }
              ]
            },
            {
              "paramid": "firstname",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User first name"
            },
            {
              "paramid": "middlename",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User middle name"
            },
            {
              "paramid": "lastname",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "''",
              "hint": "User last name"
            },
            {
              "paramid": "adresssname",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User address name"
            },
            {
              "paramid": "title",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User title"
            },
            {
              "paramid": "country",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "''",
              "hint": "User country"
            },
            {
              "paramid": "state",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User state"
            },
            {
              "paramid": "adress1",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User adress line 1"
            },
            {
              "paramid": "adress2",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User adress line 2"
            },
            {
              "paramid": "postcode",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "postal zip code"
            },
            {
              "paramid": "postcity",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "postal city"
            },
            {
              "paramid": "email1",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "Primary email"
            },
            {
              "paramid": "email2",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "Secondary email"
            },
            {
              "paramid": "landline",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "Secondary email"
            },
            {
              "paramid": "mobile",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "Secondary email"
            },
            {
              "paramid": "organization",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User organization"
            },
            {
              "paramid": "department",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User department"
            },
            {
              "paramid": "unit",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User unit"
            },
            {
              "paramid": "position",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "''",
              "hint": "User professional psotion"
            }
          ]
        }
      ]
    }
  ]
}
```
