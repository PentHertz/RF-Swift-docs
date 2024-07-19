.. _prebuiltcontainer:

Using a prebuilt container
==========================

Our prebuilt container are available on the Penthertz official registry (``penthertz/rfswift``). Each prebuilt is different by the number of installed tools, can be a light, or full version, or a version only for Wi-Fi, Bluetooth, RFID, or any other hardware attacks. 

.. Warning::

	It can be rare, but some tools may only be available for a specific architecture.

Listing available images
-------------------------

To get the list in live, you can use the following command:

.. code-block:: bash

	rfswift images remote
	[...]
	+--------------------+----------------------+--------------------------------------+--------------+-------------------------------------------------------------------------+
	|        TAG         |     PUSHED DATE      |                IMAGE                 | ARCHITECTURE |                                 DIGEST                                  |
	+--------------------+----------------------+--------------------------------------+--------------+-------------------------------------------------------------------------+
	| sdr_full           | 2024-07-17T18:30:54Z | penthertz/rfswift:sdr_full           | amd64        | sha256:aeea78ebdee039405905ce90dc8f642ac0484e386b320eb2215ae0b74c9d18ff |
	| sdr_light          | 2024-07-17T18:28:56Z | penthertz/rfswift:sdr_light          | amd64        | sha256:70973e503cbb225781eaeb6da9d59b15a791ec162939d7c7259065d44c013a5d |
	| corebuild          | 2024-07-17T18:28:22Z | penthertz/rfswift:corebuild          | amd64        | sha256:59f0059aac72499a721ebd22af85b53bd24dcf6caba4c7cb2ac75f83477bb2a9 |
	| bluetooth          | 2024-07-17T18:16:14Z | penthertz/rfswift:bluetooth          | amd64        | sha256:ed592ad5fbd8e62fde2e3777fc5d554a7d8097eb2f053c0798381265db56f9e7 |
	| wifi               | 2024-07-17T18:15:18Z | penthertz/rfswift:wifi               | amd64        | sha256:7d638c91f366d8d587ab339c3488ac07de95896e3e7570e212a676d386595f2a |
	| rfid               | 2024-07-17T18:13:52Z | penthertz/rfswift:rfid               | amd64        | sha256:5a693a88febe08c69ad2d4b6805283602130a19b5b7ba9a5a170c729a2187114 |
	| telecom            | 2024-07-17T17:55:16Z | penthertz/rfswift:telecom            | amd64        | sha256:8758b53ba9e2ca7b17f83769724f22f8f9e5388526376ce991aacfbe77f3fc1e |
	| automotive         | 2024-07-14T23:14:47Z | penthertz/rfswift:automotive         | amd64        | sha256:6d7bf1f82079e58de335282f61b5ef41654d4a6f7df43d5f4021d5db19a04b4f |
	| latest             | 2024-07-14T22:03:08Z | penthertz/rfswift:latest             | amd64        | sha256:0f47bd48c43bdc3c74680676caf6529dfaa76fe0860889e92368511da035a411 |
	| sdr_light_rtlsdrv4 | 2024-06-28T13:18:19Z | penthertz/rfswift:sdr_light_rtlsdrv4 | amd64        | sha256:b0d103f04e2f185c8191087a84bda17762b099b9cc2ac42cfd2504d5556815ca |
	| sdr_light_antsdr   | 2024-06-28T09:48:14Z | penthertz/rfswift:sdr_light_antsdr   | amd64        | sha256:11e5ca18edf7bd4aad92bcd359ba74e1588f2e1d9e3174d373a19121507efb56 |
	| reversing          | 2024-06-28T09:44:56Z | penthertz/rfswift:reversing          | amd64        | sha256:fd0044a2e8f22f29434484b213b37af02a787925c14f2740a6db52c1e6b94363 |
	| wifi_amd64         | 2024-06-22T17:44:24Z | penthertz/rfswift:wifi_amd64         | amd64        | sha256:e8abea79178402f83ddcf8e7d7969ac31eb49cede54915e4aeed09b29555be75 |
	| bluetooth_amd64    | 2024-06-22T17:34:42Z | penthertz/rfswift:bluetooth_amd64    | amd64        | sha256:37f9b903d84db537acdb77b425cca45eda968351835b19893f36c69d90ff0556 |
	| rfid_amd64         | 2024-06-22T17:33:19Z | penthertz/rfswift:rfid_amd64         | amd64        | sha256:57bbaf207150b7bed2f8836a7444102034bb303a3d9a353e66d6ff38570ad429 |
	| sdr_full_amd64     | 2024-06-22T17:32:17Z | penthertz/rfswift:sdr_full_amd64     | amd64        | sha256:7c0654033d52d1928c95978d6704c67f8e2898c2280b1a4c39cac87364e3201b |
	| sdr_light_amd64    | 2024-06-22T17:22:21Z | penthertz/rfswift:sdr_light_amd64    | amd64        | sha256:8abb056f4a2060255fe16b82e45b18c85735f352f2d14579ba69238b225f90d2 |
	| corebuild_amd64    | 2024-06-22T17:14:38Z | penthertz/rfswift:corebuild_amd64    | amd64        | sha256:cc8d802951ebdcf4ab4f653e1d0eb921b7ad9773e9ae78bd1791da5fe2d501ee |
	| last               | 2024-05-26T22:24:29Z | penthertz/rfswift:last               | amd64        | sha256:7aea486700938c5960503728a74b4de5ad39f84879c9eaf4746400655f8bad3c |
	| sdr_full_win11     | 2024-05-20T21:39:17Z | penthertz/rfswift:sdr_full_win11     | amd64        | sha256:024fff52e702bd2f5de26df3f8d65e48fff1d6140e3f303f299a8db8cfd82ef8 |
	| light_antsdr       | 2024-05-20T15:03:13Z | penthertz/rfswift:light_antsdr       | amd64        | sha256:cf976f8b4bf6b17640a711e0562688fd08938a7686480c4ade2dd507d7f5ad99 |
	+--------------------+----------------------+--------------------------------------+--------------+-------------------------------------------------------------------------+


Pulling images
---------------

You can pull one or more Docker images with the following command line:

.. code-block:: bash

	rfswift images pull -i penthertz/rfswift:<prebuilt container tag>


For example, if you want to pull the full images containing all the tools, you can pull the ``latest`` tag as follows:

.. code-block:: bash

	rfswift images pull -i penthertz/rfswift:latest

And if you need it for an aarch64 platform:

.. code-block:: bash

	rfswift images pull -i penthertz/rfswift:latest_aarch64


Example:

.. raw:: html

	<script src="https://asciinema.org/a/cUo633h6Q6ijO6vJfro6Tl1lW.js" id="asciicast-cUo633h6Q6ijO6vJfro6Tl1lW" async="true"></script>


If you prefer to build your own images, check :ref:`Linux<own_image>` page.

To run containers, you can go to the :ref:`next<running_container>` page.

To get the list of tools per tag, you can read the associated page :ref:`included tools <tools_per_tag>`.