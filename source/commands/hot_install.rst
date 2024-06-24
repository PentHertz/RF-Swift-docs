.. _hot_install:

install
=======

If after making your own images, or using one from ``penthertz/rfswift`` you find that an implemented tool is missing, you can always call the associated function as follows by providing the container ID on which you want to perform the installation:

.. code-block:: bash

	rfswift install -i <install function (called by entrypoint.sh)> -c <container id> [-c <container id>]


.. tip::

   This command may be perfect if by anychance you want to install GPU dependencies to finally us it.