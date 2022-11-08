.. _structure:


Organization of the I/O files and folders
==================================================

The preferred approach is to have two folders, one which will be used as output for the verbose mode, and one for the production mode.
The input (RDF graph) files should all be descendants of a unique folder. The converter will load incrementally in a single graph all .ttl files found below the starting point (exploring recursively the subfolders and following symlinks). Thus, you should remove the undesired graphs or zip them.


|--- verbose folder 
|           |
|            ---- CONCEPT_DIMENSION_VERBOSE.csv
|            ---- MODIFIER_DIMENSION_VERBOSE.csv
|            ---- migrations_logs.csv
...
|
|--- output folder
|           |
|            ---- CONCEPT_DIMENSION.csv 
|            ---- MODIFIER_DIMENSION.csv
|            ---- METADATA.csv
|            ---- TABLE_ACCESS.csv
|            ---- migrations_logs.csv
|            ---- OBSERVATION_FACT.csv
|            ---- ... <5 other CSV tables (i2b2 star schema)>
...
|
|---   graphs
|           |
|            ---- first cohort
            |                 |
            |                 ---- data_graph_1.ttl
            |                 ---- data_graph_1b.ttl
            |
             ---- second cohort
            |                 |
            |                 --- <...>
            |
            |
             ---- any_graph.ttl

               
