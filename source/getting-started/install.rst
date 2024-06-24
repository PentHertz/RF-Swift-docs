.. _rfswift_install:

Installing RF Swift
===================

To install RF Swift, you have to choice using the pre-compiled binary wrapper depending on your system and pull an existing container image, or to compile the Go project and/or the Docker images from sources.

.. warning::

 	Even if the project, could work on macOS with some manual workaround, we do not adverstise it for the moment, but this system will be a 100% supported anytime soon.

This documentation guides you through different steps you can follow to be running the project smoothly.

First, you need to get or compile the `rfswift` binary, and then pull or bake your own Docker images.

Requirements
------------

The minimum requirements to run the project are the following:


..  tabs::

    ..  group-tab:: Linux

        Docker is needed at least to run RF Swift containers. It can be directly your prefered package manager, such as APT or installed manually.

        .. tip::

           From Linux systems, Docker can be installed quickly and easily with the following command-line:

           .. code-block:: bash

              curl -fsSL "https://get.docker.com/" | sh


    ..  group-tab:: macOS

        .. warning::

            This system will be soon supported at 100%

    ..  group-tab:: Windows

		*  `Docker Desktop <https://docs.docker.com/desktop/install/windows-install/>`__ to run container
		* `usbipd <https://learn.microsoft.com/en-us/windows/wsl/connect-usb>`__ to bind USB devices to the host
		* For programs using PulseAudio, follow steps in the following `pulseaudio page <https://www.linuxuprising.com/2021/03/how-to-get-sound-pulseaudio-to-work-on.html>`_ using `new binaries here <https://pgaskin.net/pulseaudio-win32/>`_.


		.. warning::

			Make sure Docker Desktop runs in `WSL2 <https://docs.docker.com/desktop/wsl/#enabling-docker-support-in-wsl-2-distros>`__.


To begin the installation, you will have to clone the following Git project:

.. code-block:: bash

	git clone https://github.com/PentHertz/RF-Swift.git


Or you can also use one of our `precompiled binaries <https://github.com/PentHertz/RF-Swift/tags>`_ directly.


If you want to compile the project, Golang will be also a requirement, but using the provided installation script in the root directory:

..  tabs::

    ..  group-tab:: Linux

		.. code-block:: bash

			./build.sh 
			[+] Installing Go
			...
			[+] Building RF Switch Go Project
			...


    ..  group-tab:: macOS

        .. warning::

            This system will be soon supported at 100%

    ..  group-tab:: Windows

		.. code-block:: bash
		
			build-windows.bat
			[+] Installing Go
			...
			[+] Building RF Switch Go Project
			...

.. warning::

	When the installation script asks for a name to build an image (e.g: ``Enter image tag value``) you can skip it to use prebuilt Docker images to avoid long compilation time, and use ``pull`` command using ``rfswift``.


Skip Go wrapper building
-------------------------

To even avoid building the ``rfswift`` wrapper, you can use one of our precompiled binaries `available here <https://github.com/PentHertz/RF-Swift/tags>`_ (take the latest release).