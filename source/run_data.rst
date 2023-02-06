.. _run_data:


Fast-forward: convert RDF data samples
=======================================

Using docker
-------------

Once your docker image is installed (see :ref:`the installation section <installation>`, your :ref:`configuration <configuration>` is ready and the :ref:`I/O folders <structure>` are populated with the ontology tables, run:

.. code-block:: shell
   :caption: Example using a direct production run
   :emphasize-lines: 5
        
   $ ls /opt/production_tables
           MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv METADATA.csv TABLE_ACCESS.csv

   # Run the converter in production mode
   $ make up

   # Or use $(make up-d) to avoid capturing the console

   # Check the output
   $ ls /opt/production_tables
           MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv METADATA.csv TABLE_ACCESS.csv
           OBSERVATION_FACT.csv PROVIDER_DIMENSION.CSV PATIENT_DIMENSION.CSV PATIENT_MAPPING.CSV
           VISIT_DIMENSION.CSV ENCOUNTER_MAPPING.CSV


And for a verbose run:


.. code-block:: shell
   :caption: Example using a verbose run
   :emphasize-lines: 8,15 
        
   # Check the I/O folders
   $ ls /opt/verbose_tables 
          MODIFIER_DIMENSION_DEBUG.csv CONCEPT_DIMENSION_DEBUG.csv
   $ ls /opt/production_tables
          MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv METADATA.csv TABLE_ACCESS.csv

   # Run the converter in verbose mode
   $ make verbose DEBUG_FOLDER=/opt/verbose_tables

   $ cd /opt/verbose_tables
   $ cat logs_missing_modifiers.csv
          # Prints list of data items that don't match ontology items
   # If I'm happy with this (or file doesn't exist), I can move on and use this for production

   $ bash postprod.bash -verboseF /opt/verbose_tables -outputF /opt/production_tables

   # Check the output
   $ ls /opt/production_tables
          MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv 
          METADATA.csv TABLE_ACCESS.csv
          OBSERVATION_FACT.csv PROVIDER_DIMENSION.CSV 
          PATIENT_DIMENSION.CSV PATIENT_MAPPING.CSV
          VISIT_DIMENSION.CSV ENCOUNTER_MAPPING.CSV

 
From the source files
----------------------
The steps are roughly the same (here shown only for the verbose scenario). Only make sure your configuration files point to the correct folder (for this example, the */opt/verbose_tables/* folder and have the correct value for the *DEBUG* variable (*True* for this example):

.. code-block:: shell
   :caption: Example using a verbose run
   :emphasize-lines: 10,17   

   # Check the I/O folders
   $ ls /opt/verbose_tables
           MODIFIER_DIMENSION_DEBUG.csv CONCEPT_DIMENSION_DEBUG.csv
   $ ls /opt/production_tables
           MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv 
           METADATA.csv TABLE_ACCESS.csv

   # Run the converter in verbose mode
   $ cd RDF-i2b2-converter
   $ python3 src/main_data.py

   $ cd /opt/verbose_tables
   $ cat logs_missing_modifiers.csv
           # Prints list of data items that don't match ontology items
   # If I'm happy with this (or file doesn't exist), I can move on and use this for production

   $ bash postprod.bash -verboseF /opt/verbose_tables -outputF /opt/production_tables

   # Check the output
   $ ls /opt/production_tables
           MODIFIER_DIMENSION.csv CONCEPT_DIMENSION.csv 
           METADATA.csv TABLE_ACCESS.csv
           OBSERVATION_FACT.csv PROVIDER_DIMENSION.CSV 
           PATIENT_DIMENSION.CSV PATIENT_MAPPING.CSV
           VISIT_DIMENSION.CSV ENCOUNTER_MAPPING.CSV




