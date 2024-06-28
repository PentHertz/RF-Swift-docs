.. _images_command:

images
=====

The command ``images`` allows to list all images build for rfswift.


We can get the list with as follows:

.. code-block:: bash

	rfswift images
	[...]
	ID: sha256:943b7fb287994fa7bda64d5c71fce9a2c0bd128dda75dd89f6b8eb8802925fa5
	RepoTags: [penthertz/rfswift:telecom]
	Labels: map[org.container.author:Sébastien Dudek (FlUxIuS) org.container.project:rfswift org.opencontainers.image.ref.name:ubuntu org.opencontainers.image.version:22.04]

	ID: sha256:19a62c26128f7ae4649763ca658e083217d4a00de5d664cce00f681e0de49c8a
	RepoTags: [penthertz/rfswift:sdr_light_rtlsdrv4]
	Labels: map[org.container.author:Sébastien Dudek (FlUxIuS) org.container.project:rfswift org.opencontainers.image.ref.name:ubuntu org.opencontainers.image.version:22.04]

	ID: sha256:95dc13c4a859a0d5416053a8dcdaddaf64bfc5024af93da588fbe3205d7b0d70
	[...]
