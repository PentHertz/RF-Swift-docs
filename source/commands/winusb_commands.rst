.. _winusb_commands:

winusb for Windows
===================

.. warning::

   This command requires to be launch as an Administrator.


`winusb` is a set of sub command that allow to directly attach USB device to the container with ``usbipd.exe``.

Here are the supported options:

.. code-block:: bash
	
	Manage WinUSB devices

	Usage:
	  rfswift winusb [command]

	Available Commands:
	  attach      Attach a bus ID
	  detach      Detach a bus ID
	  list        List bus IDs


To list USB device on the hosts you can issue ``list`` as follows:


.. code-block:: bash

	rfswift winusb list


Which will give a list of devices and the status.

To attach the desired device to a container, you need to use ``attach`` with argument ``-i`` command as follows:

.. code-block:: bash

	rfswift winusb attach -i <usb ID like: 1-4>


You can also detach the device with the ``detach`` command.