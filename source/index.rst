.. RF Swift documentation master file, created by
   sphinx-quickstart on Mon Jun 24 11:07:59 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

RF Swift: the epic setup for RF HAMS and professionnals
=======================================================

.. raw:: html

    <div align="center">
      <img alt="RF Swift logo" width="600" src="https://github.com/PentHertz/RF-Swift-docs/blob/main/.assets/logo.png?raw=true">
      <br><br>
      <img alt="linux supported" src="https://img.shields.io/badge/linux-supported-success">
      <img alt="windows supported" src="https://img.shields.io/badge/windows-supported-success">
      <img alt="windows supported" src="https://img.shields.io/badge/macos-pending-orange">
     
      <br>
      <img alt="amd64" src="https://img.shields.io/badge/amd64%20(x86__64)-supported-success">
      <img alt="arm64" src="https://img.shields.io/badge/arm64%20(aarch64)-supported-success">
      <br><br>
      <a target="_blank" rel="noopener noreferrer" href="https://x.com/intent/follow?screen_name=FlUxIuS" title="Follow"><img src="https://img.shields.io/twitter/follow/_nwodtuhs?label=FlUxIuS&style=social" alt="Twitter FlUxIuS"></a>
      <a target="_blank" rel="noopener noreferrer" href="https://x.com/intent/follow?screen_name=Penthertz" title="Follow"><img src="https://img.shields.io/twitter/follow/_nwodtuhs?label=Penthertz&style=social" alt="Twitter Dramelac"></a>
      <br><br>
      <a target="_blank" rel="noopener noreferrer" href="https://discord.gg/4FbMfZEz" title="Join us on Discord"><img src="https://github.com/PentHertz/RF-Swift-docs/blob/main/.assets/discord_join_us.png?raw=true" width="150" alt="Join us on Discord"></a>
      <br><br>
    </div>

.. toctree::
   :maxdepth: 2
   :caption: Contents:


RF Swift is a toolbox for creating an environment laboratory for your RF assessments, that can easily fit your prerequirements.

This toolbox is probably the best solution to deploy a generic, as well as a special environment securely, skipping the headache and waste of time when installing and using RF tools on same host.

.. warning::

   This documentation is in working progress, and may be a little uncomplet for the moment, or not displayed correctly. Feel free to share your experience if you want to contribute to it!

.. warning::

   Even if the project, could work on macOS with some manual workaround, we do not adverstise it for the moment, but this system will be a 100% supported anytime soon.


The RF Swift project
---------------------

RF Swift includes different components to make RF hobbists, students/learners, professionnals, RF hackers, bug hunters' life easy.

* Go wrapper: instruments containers and hosts to simplify the use of tools that may require internet connectivity, display, sounds, USB accesses. This `rfswift` is the main program you will interact with to run clean containers, execute inside running or paused containers, and do many magic actions that will make things work without headache.
* Docker images: some pre-built Docker container images are available in RF Swift's repository. In case you wan to bake your own environment, preserve some spaces, and have a special set-up, you will also find some Docker files you can edit to fit your expectations.


How to begin?
--------------

It is probably the time for you to try, and to make your like easy in this task, you can go through our documentations, and first install RF Swift based on your OS: :ref:`Linux<rfswift_install>` or :ref:`Windows<rfswift_install>`.



Community
---------

You feel inspired and want to share you cakes, or you have an issues to report or a patch, feel free to use the RF Swift `our repository <https://github.com/PentHertz/RF-Swift/>`_ or `RF Swift discord <https://discord.gg/4FbMfZEz>`_.


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Quick start

   getting-started/install.rst
   getting-started/prebuiltcontainer.rst
   getting-started/running_image.rst
   getting-started/tools_per_tag.rst


.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: From source install

   getting-started/own_image.rst


.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: RF Swift's commands

   commands/run_command.rst
   commands/exec_command.rst
   commands/last_containers.rst
   commands/hot_install.rst
   commands/commit_change.rst
   commands/renaming_images.rst
   commands/removing_containers.rst
   commands/delete_command.rst
   commands/images_command.rst
   commands/winusb_commands.rst