.. _run_command:

run
===

To command ``run`` has some options:


.. code-block:: bash
	
	rfswift run --help
	[...]
	Usage:
	  rfswift run [flags]

	Flags:
	  -b, --bind string      extra bindings (separate them with commas)
	  -e, --command string   command to exec (default: '/bin/bash')
	  -d, --display string   set X Display (default: 'DISPLAY=:0')
	  -h, --help             help for run
	  -i, --image string     image (default: 'myrfswift:latest')


Binding a directory
--------------------

If needed, for example when using a PlutoSDR device, you can add some more bindings than those used by default:

.. code-block:: bash

	rfswift run -b "/run/dbus/system_bus_socket:/run/dbus/system_bus_socket,/dev/snd:/dev/snd,/dev/dri:/dev/dri"


.. tip::

	This binding option may be perfect if you do not want to commit any changes of your container, but need at least results by making a sharing directory as follows:

	.. code-block:: bash

   		/home/fluxius/Project/RF-Swift/HWIO2024/part1/Labs:/root/Lab