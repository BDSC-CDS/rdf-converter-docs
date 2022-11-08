.. _run_ontology:

Fast-forward: convert a RDF ontology graph
===========================================

Using Docker
--------------

Once your docker image is installed (see :ref:`the installation section <installation>`, your :ref:`configuration <configuration>` is ready and the :ref:`I/O folders <structure>` are created and populated by optional instruction files:

.. code-block:: shell
   :caption: Example using a direct production run
   :emphasize-lines: 5

   $ ls /opt/production_tables
          lookup_units.csv

   # Run the converter in production mode
   $ make up

   # Or use $(make up-d) to avoid capturing the console

   # Check the output
   $ ls /opt/production_tables
          MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv 
          METADATA.csv TABLE_ACCESS.csv 
          lookup_units.csv (migrations_logs.csv)


.. code-block:: shell
   :caption: Example using a verbose run
   :emphasize-lines: 6

   # Check the I/O folders
   $ ls /opt/verbose_tables
          lookup_units.csv 

   # Run the converter in verbose mode
   $ make verbose DEBUG_FOLDER=/opt/verbose_tables ONTOLOGY_LOCATION=/opt/ontology_rdf_graphs

   # Check the output
   $ ls /opt/verbose_tables
          MODIFIER_DIMENSION_VERBOSE.csv CONCEPT_DIMENSION_VERBOSE.csv 
          METADATA.csv TABLE_ACCESS.csv 
          lookup_units.csv (migrations_logs.csv)



From the source files
-----------------------
