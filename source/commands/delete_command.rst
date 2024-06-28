.. _delete_command:

delete
======

The command ``delete`` has some options:

.. code-block:: bash
	
	rfswift delete --help
	[...]
	Usage:
	  rfswift delete [flags]

	Flags:
	  -h, --help           help for delete
	  -i, --image string   image ID or tag



To remove an image, you can issue the command ``delete`` documented using ``-i`` argument to precise the image ID or tag.

.. code-block:: bash

	rfswift delete -i super:tag
