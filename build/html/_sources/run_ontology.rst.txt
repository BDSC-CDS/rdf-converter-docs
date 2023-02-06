.. _run_ontology:

Fast-forward: convert a RDF ontology graph
===========================================
.. important::

        The main requirements for an ontology to be converted in the current version are:
        
        1. The ontology graph contains NO CYCLES (navigating with the subclass/domain/range properties should not allow to come back to the same point) 
        
        2. All classes on which a property applies are EXPLICITLY listed in this property's domain.
                   
        3. No class has both subclasses and properties (no class is both an object for subclassOf and domain predicates)

Using Docker
--------------

Once your docker image is installed (see :ref:`the docker building section <docker>`, your :ref:`configuration <configuration>` is ready and the :ref:`I/O folders <structure>` are created and populated by optional instruction files:

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
**Check the src/utils.py file points to the correct configuration files.**

Then steps are here shown only for the verbose scenario (production one is the same, with DEBUG set to False in the configuration). Make sure your configuration files point to the correct folder (for this example, the /opt/verbose_tables/ folder) and have the correct value for the DEBUG variable (True for this example):

.. code-block:: shell
   :caption: Example using a verbose run
   :emphasize-lines: 7 

   # Check the I/O folders
   $ ls /opt/verbose_tables
          lookup_units.csv 

   # Run the converter in verbose mode
   $ cd RDF-i2b2-converter
   $ python3 src/main_ontology.py
   
   # Check the output
   $ ls /opt/verbose_tables
           MODIFIER_DIMENSION_VERBOSE.csv CONCEPT_DIMENSION_VERBOSE.csv 
           METADATA.csv TABLE_ACCESS.csv 
           lookup_units.csv (migrations_logs.csv)

