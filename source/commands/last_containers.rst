.. _last_containers:

Displaying last containers
==========================

To get the last 10 containers you have created, you can use the following command:

.. code-block:: bash

	rfswift last

To display specific images, you can filter results with the ``-f`` argument as follows:

.. code-block:: bash

	rfswift last -f myrfswift:latest # using a filter for images
	
