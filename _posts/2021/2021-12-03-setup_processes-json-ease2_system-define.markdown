---
layout: article
title: ease2_system-define_v090.json
categories: setup_processes
excerpt:  Define the EASE-grid 2 tile/project systems
tags:: 
    - json/ease2_system-define
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/ease2 system define (setup_processes)

###  Define the EASE-grid 2 tile/project systems

The json command file <span class='file'>ease2_system-define_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
      "processid": "DefineCustomSystem",
      "overwrite": false,
      "version": "0.9",
      "verbose": 3,
      "parameters": {
        "systemid": "ease2n",
        "epsg": 6931,
        "minx": -9000000,
        "miny": -9000000,
        "maxx": 9000000,
        "maxy": 9000000,
        "xtiles": 20,
        "ytiles": 20
      }
    }
  ]
}
```
