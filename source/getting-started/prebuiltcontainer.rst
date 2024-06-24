.. _prebuiltcontainer:

Using a prebuilt container
==========================

Our prebuilt container are available on the Penthertz official registry (``penthertz/rfswift``). Each prebuilt is different by the number of installed tools, can be a light, or full version, or a version only for Wi-Fi, Bluetooth, RFID, or any other hardware attacks. 

Here is a list of tag you can find:

.. tabularcolumns:: |p{1cm}|p{7cm}|

.. csv-table:: Prebuilt images
   :file: supportedimages.csv
   :header-rows: 1
   :class: longtable


.. Warning::

	It can be rare, but some tools may only be available for a specific architecture.


You can pull one or more Docker images with the following command line:

.. code-block:: bash

	rfswift pull penthertz/rfswift:<prebuilt container tag>


For example, if you want to pull the full images containing all the tools, you can pull the ``latest`` tag as follows:

.. code-block:: bash

	rfswift pull penthertz/rfswift:latest


If you want just something specific to SDR and full:

.. code-block:: bash

	rfswift pull penthertz/rfswift:sdr_full


Or something specific to Wi-Fi:

.. code-block:: bash

	rfswift pull penthertz/rfswift:wifi

And if you need it for an aarch64 platform:

.. code-block:: bash

	rfswift pull penthertz/rfswift:wifi_aarch64


If you prefer to build your own images, check :ref:`Linux<own_image>` page.

To run containers, you can go to the :ref:`next<running_container>` page.

To get the list of tools per tag, you can read the associated page :ref:`included tools <tools_per_tag>`.