.. _running_container:

Running a container
===================

To run a container, you can directly use the tag associated to the image you have pulled or built.


To run a container, use the command ``./rfswift run -h`` to see the needed arguments:


.. code-block:: bash

	[...]
	Usage:
	  rfswift run [flags]

	Flags:
	  -b, --bind string      extra bindings (separate them with commas)
	  -e, --command string   command to exec (default: '/bin/bash')
	  -d, --display string   set X Display (default: 'DISPLAY=:0')
	  -h, --help             help for run
	  -i, --image string     image (default: 'myrfswift:latest')


By default, you can directly use the ``run`` command with the tag name of your choice, such as ``penthertz/rfswift:sdr_full`` as follows:

..  tabs::

	..  group-tab:: Linux

		.. code-block:: bash

			sudo ./rfswift run -i penthertz/rfswift:sdr_full


		.. warning::

			`Docker "Rootless mode <https://docs.docker.com/engine/security/rootless/>`_" is not supported by RF Swift as of yet. Please follow the install procedure mentionned above.


		.. tip::

			You can use interpreter's script such as ``bashrc`` to run ``rfswift`` with ``sudo``:

			.. code-block:: bash

				echo "alias exegol='sudo -E $(which <path of rfswift>)'" >> ~/.bash_aliases 
				source ~/.bashrc

		.. warning::

			Great power requires great responsabilities, always try checking if you are running the right tool with ``sudo``.

	..  group-tab:: macOS

		.. warning::

			This system will be soon supported at 100%

	..  group-tab:: Windows

		.. code-block:: bash

			rfswift.exe run -i penthertz/rfswift:sdr_full

		.. warning::

			Docker Desktop doesn't require administrator privileges.


		To attach a USB device, you'll need to install and use `usbipd <https://learn.microsoft.com/en-us/windows/wsl/connect-usb>`_ tool as follows by first listing devices plugged in the computer:

		.. code-block:: bash

			usbipd wsl list

		And then bind and attach the identified USB devices you want on the container:

		.. code-block:: bash
		
			usbipd bind --busid <busid>
			usbipd attach --wsl --busid <busid>

		Demo: 

		.. raw:: html

			<video width="320" height="240" controls>
		  	<source src="/.assets/331809901-bb2ccd96-b688-4106-8fba-d82f84ff1ea4.mp4" type="video/mp4">
			Your browser does not support the video tag.
			</video>

To run a specific command when starting a new container, you can use ``-e`` argument as follows if you want to run the ``sdrpp`` (SDR++) application:

.. code-block:: bash

	rfswift run -i penthertz/rfswift:sdr_full -e sdrpp



Getting the sound
''''''''''''''''''

Some applications may require ``pulseaudio`` to be running. 
To avoid any specific configuration for each plateform (Windows, macOS, Linux), we recommended to use ``pulseaudio`` in TCP with a defined port.

After we can use the ``PULSE_SERVER`` environment variable to tell to our program we are launching such as ``gqrx`` for example:


.. code-block:: bash

	PULSE_SERVER=tcp:<host IP address>:34567 gqrx

.. tip::

	This step is manual but will be automated in next version of the ``rfswift`` tool.