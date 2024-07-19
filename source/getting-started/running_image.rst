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

				echo "alias rfswift='sudo -E $(which <path of rfswift>)'" >> ~/.bash_aliases 
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


		To attach a USB device, you can our documented :ref:`winusb<winusb_commands>` to simplify USB device attachment on the container. Or you can also manually use `usbipd <https://learn.microsoft.com/en-us/windows/wsl/connect-usb>`_ tool as follows by first listing devices plugged in the computer:

		.. code-block:: bash

			usbipd wsl list

		And then bind and attach the identified USB devices you want on the container:

		.. code-block:: bash
		
			usbipd bind --busid <busid>
			usbipd attach --wsl --busid <busid>


To run a specific command when starting a new container, you can use ``-e`` argument as follows if you want to run the ``sdrpp`` (SDR++) application:

.. code-block:: bash

	rfswift run -i penthertz/rfswift:sdr_full -e sdrpp



Getting the sound
''''''''''''''''''

Some applications may require ``pulseaudio`` to be running. 
To avoid any specific configuration for each plateform (Windows, macOS, Linux), we recommended to use ``pulseaudio`` in TCP with a defined port.

This is done by default when running a container, and allowing accesses on your host with the following command:

.. code-block:: bash

	./rfswift host audio enable # To execute as a simple user!

.. warning::

	This command should be run as a simple user.

But you experience issue, look on the container if the ``PULSE_SERVER`` environment variable is set as follows:

.. code-block:: bash

	PULSE_SERVER=tcp:<host IP address>:34567 gqrx

And also look if pulseaudi is well installed in your computer.

For Windows users, you will have to `install pulseaudio for Windows and set <https://www.freedesktop.org/wiki/Software/PulseAudio/Ports/Windows/Support/>`_ ``$INSTALL_DIR/etc/pulse/default.pa`` as follows:

.. code-block:: bash

	load-module module-native-protocol-tcp auth-ip-acl=$HOST_IP