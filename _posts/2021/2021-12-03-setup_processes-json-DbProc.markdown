---
layout: article
title: DbProc_v090.json
categories: setup_processes
excerpt:  Install Database processes (export, import, dump etc )
tags:: 
    - json/DbProc
date: 2021-12-03
modified: 2021-12-03
comments: true
share: true
---

# json/DbProc (setup_processes)

###  Install Database processes (export, import, dump etc )

The json command file <span class='file'>DbProc_v090.json</span> is part of karttur's GeoImagine project <span class='project'>setup_processes</span>. Calling the json file will execute the following commands of the GeoImagine Framework.

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
        "rootprocid": "DatabaseProc",
        "title": "Database processing",
        "label": "Database processing"
      }
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "ExportTableCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Export Db table as csv",
        "label": "Export Db table as csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "regions"
            },
            {
              "paramid": "columns",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "*",
              "hint": "list of columns to include, set * to include all"
            },
            {
              "paramid": "wherestatement",
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "InsertTableCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Insert indivudual Db records for table from csv",
        "label": "Insert indivudual Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "regions"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "InsertSchemaCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Insert indivudual Db records for table from csv",
        "label": "Insert indivudual Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "InsertDatabaseCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Insert indivudual Db records for table from csv",
        "label": "Insert indivudual Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "CopyTableCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "COPY Db records for table from csv",
        "label": "COPY Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "regions"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "CopySchemaCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "COPY Db records for table from csv",
        "label": "COPY Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "CopyDatabaseCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "COPY Db records for table from csv",
        "label": "COPY Db records for table from csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "csv"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "ExportSchemaCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Export Db schema as individual tables with csv",
        "label": "Export Db schema as individual tables with csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "ExportDatabaseCsv",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Export Db as individual tables with csv",
        "label": "Export Db sas individual tables with csv"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "dummy",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "DumpTableSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Dump Database table",
        "label": "Dump Database table"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "regions"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "RestoreTableSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Restore Database table",
        "label": "Restore Database table"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "table",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "regions"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "DumpSchemaSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Dump Database schema",
        "label": "Dump Database schema"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "RestoreSchemaSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Restore Database schema",
        "label": "Restore Database schema"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "schema",
              "paramtyp": "text",
              "required": true,
              "defaultvalue": "system"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "DumpDatabaseSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Dump Database",
        "label": "Dump Database"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    },
    {
      "processid": "addsubproc",
      "overwrite": false,
      "parameters": {
        "rootprocid": "DatabaseProc",
        "subprocid": "RestoreDatabaseSQL",
        "version": "0.9.0",
        "minuserstratum": 10,
        "title": "Restore Database",
        "label": "Restore Database"
      },
      "system": [
        {
          "system": "system",
          "srcsystem": "system",
          "dstsystem": "system",
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
              "paramid": "host",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "localhost"
            },
            {
              "paramid": "format",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "c"
            },
            {
              "paramid": "cmdpath",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "None"
            },
            {
              "paramid": "dataonly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "definitiononly",
              "paramtyp": "bool",
              "required": false,
              "defaultvalue": "false"
            },
            {
              "paramid": "datum",
              "paramtyp": "text",
              "required": false,
              "defaultvalue": "0"
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
              "defaultvalue": "sql"
            }
          ]
        }
      ]
    }
  ]
}
```
