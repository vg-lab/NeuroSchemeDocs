.. note::
   This manual is still under development and there are some incomplete parts, marked as 'Work in progress'.

========================
NeuroScheme Introduction
========================

**NeuroScheme** is a visual exploratory framework that facilitates the process of knowledge extraction from complex neural scenes. This framework contains a multilevel structure, following the different organizational levels of the brain. Schematic or iconic symbols have been designed to portray the entities at each level, providing graphical representations that emphasize relevant features while hiding less important information. These schematic views, together with a multilevel organization, allow the exploration of the brain at different scales, combining in the same view different levels of abstraction whose entities can be either schematically represented (at different abstraction levels) or geometrically depicted at the finest level of detail.

--------------
External Links
--------------

The homepage for NeuroScheme is located at `NeuroScheme Homepage`_ and the source code for the latest release is available in the `Github page`_. For reporting bugs please use the `Github Issues`_ page. If you have any questions or suggestions about ViSimpl refer to dev@vg-lab.es.

.. _NeuroScheme Homepage: https://www.gmrv.es/neuroscheme/
.. _Github page: https://github.com/vg-lab/NeuroScheme
.. _Github Issues: https://github.com/vg-lab/NeuroScheme/issues

---------------------------
NeuroScheme synchronization
---------------------------

For NeuroScheme to synchronize with other applications a ZeroEQ discovery provider must be installed in the machine. ZeroEQ applications are linked using automatic discovery based on ZeroConf protocol or through explicit connection addressing using hostname and port because of that a service like Avahi on Linux or dnssd on Mac/Windows (like `Bonjour <https://developer.apple.com/bonjour/>`_) must be installed. If that service is not present NeuroScheme will still be usable but won't be able to synchronize events or selection data.

------------------------
Installation and running
------------------------

NeuroScheme can be downloaded from the `NeuroScheme Homepage`_ for Linux and Mac operating systems and executed locally. Additionally it can be executed using a docker image. 

^^^^^^^^^^^^^^^^^
Executing locally
^^^^^^^^^^^^^^^^^

The application options and parameters are:

+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| **OPTION**             | **PARAMETER**                   | **DESCRIPTION**                                                                          |
+========================+=================================+==========================================================================================+
| ``--version``          | *none*                          | Shows the version of the application.                                                    |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``--help``             | *none*                          | Shows the options and arguments used                                                     |
|                        |                                 | for executing the application.                                                           |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-ncl``               | *none*                          | Do not use colors in the application                                                     |
|                        |                                 | log.                                                                                     |
| ``--not-colored-log``  |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-d``                 |  **cortex|congen**              | Specifies the data domain.                                                               |
|                        |                                 |                                                                                          |
| ``--domain``           |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-sc``                | *numerical value*               | Specifies the scale of the data.                                                         |
|                        |                                 | Default is 1.0f.                                                                         |
| ``--scale``            |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-l``                 | *path_to_log_file*              | Specifies the path of the log file.                                                      |
|                        |                                 |                                                                                          |
| ``--log-file``         |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``--json``             | *path_to_json_file*             | Load JSON data file.                                                                     |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-bc``                | *path_to_bc_file*               | Load BlueConfig file.                                                                    |
|                        |                                 | Only valid for **cortex** domain.                                                        |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-xml``               | *path_to_xml_file*              | Load XML scene.                                                                          |
|                        |                                 | Only valid for **cortex** domain.                                                        |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-target``            | *target_label*                  | Specifies target label of                                                                |
|                        |                                 | the BlueConfig file.                                                                     |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``--no-morphologies``  | *none*                          | No morphologies.                                                                         |
|                        |                                 | Only valid for **cortex** domain.                                                        |
| ``-nm``                |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``-lc``                | *none*                          | Load connectivity.                                                                       |
|                        |                                 | Only valid for **cortex** domain.                                                        |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+
| ``--csv-neuron-stats`` | *path_to_csv_file*              | Load neuron stats.                                                                       |
|                        |                                 | Only valid for **cortex** domain.                                                        |
| ``-cns``               |                                 |                                                                                          |
+------------------------+---------------------------------+------------------------------------------------------------------------------------------+

If the options are incompatible or its parameters invalid the application will abort the execution and will show the help message in the console. 

^^^^^^^^^^^^
Test dataset
^^^^^^^^^^^^

A test data for NeuroScheme (for Congen and Cortex domains) can be downloaded from: 

* https://vg-lab.es/apps/NeuroScheme/example-data/neuroscheme-congen-example-data.json
* https://vg-lab.es/apps/NeuroScheme/example-data/neuroscheme-cortex-example-data.xml
* http://neuromorpho.org/dableFiles/allen%20cell%20types/CNG%20version/H16-03-001-01-09-01_559391771_m.CNG.swc

^^^^^^^^^^^^^^
Docker example
^^^^^^^^^^^^^^

When Using a docker image replace the folder **$(pwd)/neuroscheme-example-data** by the the local folder with your local data. 

.. code-block:: bash
  :linenos:
  :emphasize-lines: 10,12

   # Pull the image
   docker pull vglab/neuroscheme:0.4.0-nvidia-ubuntu-16.04
   # Download example data
   mkdir neuroscheme-example-data && cd neuroscheme-example-data
   wget https://vg-lab.es/apps/NeuroScheme/example-data/neuroscheme-congen-example-data.json
   wget https://vg-lab.es/apps/NeuroScheme/example-data/neuroscheme-cortex-example-data.xml
   wget http://neuromorpho.org/dableFiles/allen%20cell%20types/CNG%20version/H16-03-001-01-09-01_559391771_m.CNG.swc
   cd ..
   # Run cortex example
   docker run --gpus 1 -ti --rm -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v /etc/machine-id:/etc/machine-id -v $(pwd)/neuroscheme-example-data:/data  --privileged vglab/neuroscheme:0.4.0-nvidia-ubuntu-16.04 /usr/bin/NeuroScheme -d cortex -xml /data/neuroscheme-cortex-example-data.xml
   # Run congen example
   docker run --gpus 1 -ti --rm -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v /etc/machine-id:/etc/machine-id -v $(pwd)/neuroscheme-example-data:/data  --privileged vglab/neuroscheme:0.4.0-nvidia-ubuntu-16.04 /usr/bin/NeuroScheme -d congen --json /data/neuroscheme-congen-example-data.json

.. note::
   If running the docker image you get the error  ``No protocol specified``  the following command must be executed before the docker command:

   .. code-block:: bash

      xhost local:root
