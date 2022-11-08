.. _installation:

Installation from Python source files
===============================================================

This is the documentation page for the installation of the RDF-i2b2 converter **from the source files**. It is the recommended approach if you are a developer and you want to adapt the code to your specific RDF or output design. It is also the way to go if you do not want to use Docker or any other related system.

You will need to have Python 3.7 or more recent installed, with the following dependencies:

* pandas==1.3.4

* rdflib==6.0.2

* psutil==5.9.2


Then, you need to **modify** the src/utils.py file so the three variables *GRAPH_CONFIG*, *DATA_CONFIG*, *I2B2_MAPPING* match the paths to your config files. Example config files are provided in the *local_config_template/* folder at the root of the repository. To use them as is, simply change */config/* in *src/utils.py* for "*local_config_templates/*.

Details about how to modify the configuration files are described on the :ref:`Configuration page <configuration>`.
Also make sure the :ref:`folder structure <structure>` makes sense regarding the configuration you just defined.

Then, choose to run either the :ref:`ontology converter <run_ontology>` or the :ref:`data samples converter <run_data>`. Run instructions from source files is specified on the dedicated pages.

