.. RDF-i2b2-converter documentation master file, created by
   sphinx-quickstart on Thu Sep  8 10:32:16 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to RDF-i2b2-converter's documentation!
==============================================

The converter allows you to **turn a RDF knowledge graph into a set of CSV tables fitting the i2b2 common model**.
An **ontology** converter turns the RDF ontology into i2b2 metadata content (ONT cell tables).
A **data samples** converter turns the RDF instances into i2b2 star schema (CRC cell tables).
Both can be used independently, albeit comparing the consistency of their outputs is a good idea.


Docker configurations for both modules are available and described in the associated page of this documentation. Yet, you can also run the converter(s) from the Python source files.
The main advantage of user the Docker releases is easy input/output file management and little amount of user configuration.

**Quality assessment of the data samples conversion requires comparison against the converted ontology records.** It is then recommended to run the ontology conversion first. 

**Conversion scenario (ontology or data samples conversion):**

1. Clone the relevant repository (see :ref:`Requirements and installation <reqs>`) 
2. Arrange your input files and output folders according to the predefined structure (see :ref:`I/O folders structure <structure>`)
3. Modify the provided configuration files if necessary (see :ref:`Configuration <index_configuration>`)
4. Run the converter (:ref:`data converter instructions <run_data>`, :ref:`ontology converter instructions <run_ontology>`) and check the results :ref:`Debug <verbose>` if necessary.


.. _reqs:
Requirements and installation
=============================

Using Docker
------------

`Repository for the ontology converter (Docker) <https://github.com/CHUV-DS/docker-ontology-converter>`_

`Repository for the data samples converter (Docker) <https://github.com/CHUV-DS/docker-data-converter>`_


To run the Dockerized converter(s) *smoothly*, you need to have installed
- Docker and ``make``
- Internet access from inside your container (automatic ``git pull`` at container startup)
Then, please follow the instructions in the :ref:`dedicated page <docker>`.

Exotic setups (Singularity, offline container, docker-compose instead of make, etc.) will also work if you know what you are doing (explore the Dockerfile and Makefile and adapt their content for your use).

Using Python and shell source files
-------------------------------------
`Repository of the source code <https://github.com/CHUV-DS/RDF-i2b2-converter>`_

To run the source files directly, you need to have installed

* Python >= 3.7 
* rdflib >= 6.0.2
* pandas >= 1.3.4
* psutils >= 5.9.2 (for memory monitoring)

In this case, follow the instructions of the :ref:`dedicated page <installation>`.

.. _index_configuration:
Configuration
==================
The converter comes from three configuration files read by the source code. If using a container, the config directory should be mounted as a shared volume with your host (see how to do this in the :ref:`Makefile section of the Docker deployment instructions <Makefile>`).
All the details about every configuration file are described on :ref:`this page <configuration>`, either for ontology or data conversion.

Verbose mode
============
A *verbose* mode is available, which will output human-readable identifying codes for i2b2 concepts and modifiers, instead of hashes. This is useful to assert the ontology and data converter worked consistently (and also that the input RDF data is consistent with the input RDF ontology).
We recommend to start by a *verbose* run and read the run logs. See how to do it and interpret the results :ref:`in the dedicated page <verbose>`. For the data samples conversion, if you are happy with the logs, you will be able to convert the verbose output into production-ready tables easily.
You can also bypass the *verbose* run and issue directly your tables in production mode.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   docker
   installation
   structure
   configuration
   verbose
   run_data
   run_ontology
   flowchart

* :ref:`search`
