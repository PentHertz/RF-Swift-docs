.. _exec_command:

exec
===

To command ``exec`` has some options:

.. code-block:: bash
	
	rfswift exec --help
	[...]
	Usage:
	  rfswift exec [flags]

	Flags:
	  -e, --command string     command to exec (required!)
	  -c, --container string   container to run
	  -h, --help               help for exec
	  -i, --install string     install from function script (e.g: 'sdrpp_soft_install')


To get the container ID of a previous session, you can issue the command ``last`` documented :ref:`here<last_containers>`.

Once you have the desired container ID, you can execute a command inside a running or paused container as follows:

.. code-block:: bash

	rfswift exec -c 83471263e5e5f9951d83ec27dec37ff5273f92411830b3a08d4053c05b773fe7 -e urh


.. warning::

   This command will likely fail if you issue it against a Docker container associated to a build process.