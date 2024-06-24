.. _own_image:

Building your own image
==========================

RF Swift provides the Dockerfile to create the same images available in ``penthertz/rfswift`` registry.

You can feel free to recompile, edit, or create your own images based on your RF Swift framework.


Building provided Docker images
-------------------------------

You can use the building script provided in the root directory to build a specific Docker file:

..  tabs::

    ..  group-tab:: Linux

		.. code-block:: bash

			./build.sh 
			...
			[+] Building RF Switch Go Project
			Enter image tag value (default: myrfswift:latest):  # or use a different tag value
			Enter value for Dockerfile to use (default: Dockerfile): # or use a different Dockerfile path

    ..  group-tab:: macOS

        .. warning::

            This system will be soon supported at 100%

    ..  group-tab:: Windows

		.. code-block:: bash
		
			build-windows.bat
			...
			[+] Building RF Switch Go Project
			Enter image tag value (default: myrfswift:latest):  # or use a different tag value
			Enter value for Dockerfile to use (default: Dockerfile): # or use a different Dockerfile path


Other the build is finish, you can directly use the tag ``myrfswift:latest`` for example to :ref:`run a built image<running_container>`.

The ``Dockerfile`` file present in the root directory is a default ``Dockerfile`` that builds the whole project entirelly. 

RF Swift also has some other files in the ``Dockerfiles`` directory to indepedently build images by topics.


Provided Docker files (separated Multi-stages)
-----------------------------------------------

You can also build all images using our separated Multi-stage ``Dockerfiles`` directory which builds each images by topic, avoiding the recompilation of the whole project for small changes for deep sub-layers.

..  tabs::

    ..  group-tab:: Linux

		.. code-block:: bash

			cd Dockerfiles
			make build # for all, or make sdr_light|sdr_full|bluetooth|rfid|wifi 

    ..  group-tab:: macOS

        .. warning::

            This system will be soon supported at 100%

    ..  group-tab:: Windows

		.. code-block:: bash
		
			cd Dockerfiles
			build_windows.bat build # for all, or make sdr_light|sdr_full|bluetooth|rfid|wifi 



Enabling options
----------------

Some options have been disabled for the moment, to avoid any conflicts, especially for SDR devices like ANTSDR using the UHD driver, or the RTL-SDR v4 that uses a specific driver.

To enable them, you will have to disable original options has follows before building your own images:


.. code-block:: bash

	#RUN ./entrypoint.sh rtlsdr_devices_install
	RUN ./entrypoint.sh rtlsdrv4_devices_install # optional, remove rtlsdr_devices_install if you are using the v4 version
	#RUN ./entrypoint.sh uhd_devices_install
	RUN ./entrypoint.sh antsdr_uhd_devices_install # Disable orignal UHD

Some other options are also disabled to avoid unnessary setup like the OOT modules gr-fosphor which requires GPU:

.. code-block:: bash

	# Installing gr-fosphor with OpenCL
	RUN ./entrypoint.sh grfosphor_grmod_install

.. warning::

	When enabling options that needs GPU, it is recommanded to enable GPU options as well:

		.. code-block:: bash

			# Installing OpenCL
			## NVidia drivers
			#RUN apt-fast install -y nvidia-opencl-dev nvidia-modprobe
			## Installing Intel's OpenCL
			#RUN apt-fast install -y intel-opencl-icd ocl-icd-dev ocl-icd-opencl-dev


Saving time with multi-stage pre-built images
-----------------------------------------------

To save time, feel also free using ``penthertz/rfswift`` prebuilt images tags as follows:

.. code-block:: text

	FROM corebuild:latest
	RUN echo 'APT::Install-Suggests "0";' >> /etc/apt/apt.conf.d/00-docker
	RUN echo 'APT::Install-Recommends "0";' >> /etc/apt/apt.conf.d/00-docker

	RUN apt-fast update

	COPY scripts /root/scripts/
	COPY rules /root/rules/
	COPY config /root/config/

	WORKDIR /root/scripts/
	RUN chmod +x entrypoint.sh

	# Installing Devices 

	## Installing rtlsdrv4
	RUN ./entrypoint.sh rtlsdrv4_devices_install

	## Installing SDR++
	RUN ./entrypoint.sh sdrpp_soft_fromsource_install