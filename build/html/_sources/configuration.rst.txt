.. _configuration:

Organization of the config files
================================

graph_config.json
-----------------------
This configuration file helps piloting the RDF graphs parsing and discovery. It is used by both the ontology converter and the data converter. It defines the RDF terms to be expected in the graph, the reserved URIs, etc. It also features a lookup table for terminology RDF graphs, so they can be loaded by the ontology converter in a distinct memory slot as the main ontology graph, speeding up the computations.
The fields are as follow:

.. csv-table:: Field description of graph_config
        :file: _tables/graph_config_doc.csv
        :widths: 30, 70

data_config.json
-----------------------
This file is only used by the data converter.
It therefore specifies a data-specific blacklist, the path to the data and dependencies graphs, and describes the mappings for RDF contextual fields that are not featured in the i2b2 ontology.
It contains structured instructions about how these fields should be unpacked and mapped to specific table and columns of the i2b2 star schema.

.. csv-table:: Field description of graph_config
        :file: _tables/data_config_doc.csv
        :widths: 30, 70

i2b2_rdf_config.json
----------------------
This file describes the bindings between RDF datatypes and i2b2 table-columns, and defines additional filters for ontology elements that should or should not appear in the final ontology.

.. csv-table:: Field description of i2b2_rdf_config
        :file: _tables/i2b2_config_doc.csv
        :widths: 30, 70


