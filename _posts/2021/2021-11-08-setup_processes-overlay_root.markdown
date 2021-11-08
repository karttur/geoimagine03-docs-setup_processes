---
layout: article
title: overlay_root_v090.json
categories: setup_processes
excerpt:  Install root process for overlay
tags:: 
    - overlay_root
date: 2021-11-08
modified: 2021-11-08
comments: true
share: true
---

# overlay root (setup_processes)

###  Install root process for overlay

The json command file <span class='file'>overlay_root_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "Overlay",
        "title": "Raster Overlay",
        "label": "Raster Overlay"
      }
    }
  ]
}
```
