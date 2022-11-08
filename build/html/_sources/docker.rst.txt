.. _docker:

Docker usage
===============================

The two converters are available in dedicated docker releases and work using a Docker image (either precompiled or to build locally), and a set of Makefile recipes that will help you manage the container while mounting the necessary Docker volumes. The volumes are useful to bind files (config, data source, utility, etc.) from your host to the container at startup.


Ontology converter docker
-------------------------
The docker source files are available on `Github (ontology converter) <https://github.com/CHUV-DS/docker-ontology-converter.git>`_.
Make sure your folder structure is correct (see :ref:`the dedicated section <structure>`) and then run the desired recipe from the Makefile. 

Data converter docker
----------------------
The docker source files are available on `Github (data converter) <https://github.com/CHUV-DS/docker-data-converter.git>`_.
Make sure your folder structure is correct (see :ref:`the dedicated section <structure>`) and then run the desired recipe from
the Makefile.

.. _Makefile:

Installation using the Makefile
--------------------------------
Requirements: gcc make. If not available, simply execute the command lines that are in the Makefile, as they are very explicit.

The instructions in the Makefile will help you define the local variables pointing to your local directories. 

Get the docker image by running

.. code-block:: console

   make build
       
Run the container by executing either     

.. code-block:: console

   make up-d
   # Or 
   make debug

Common fails at runtime:
------------------------
.. code-block:: console

        pop from empty list

This one means your source RDF files were not found. Check the environment variables defined in the Makefile.     

.. code-block:: console

        Conversion passed but consistency check were not performed due to absence of ontology tables (CONCEPT_DIMENSION and/or MODIFIER_DIMENSION in the folder)

Check the CONCEPT_DIMENSION and MODIFIER_DIMENSION (with trailing "_VERBOSE" if verbose mode) are in the destination folder. Check ( ``$ head -1 $file`` )  the column labels are upper-case.

