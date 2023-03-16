# nextcloud-podman-kube

Run Nexcloud with MariaDB using Podman's play kube functionality.

I wanted to take the `docker-compose.yml` examples in the Docker documentation
for Nextcloud and run it in Podman using `podman play kube`. It works, and
there were some gotchyas along the way such as making sure you assume no
defaults and everything is populated.

The first example, I'm using two separate Pod definitions. First one is for
MariaDB and it's Persistent Volume Claim. This allows the database to come
up and be ready for Nextcloud. Second, the Nextcloud container starts and
uses the MariadB Pod.

In order for these two Pods to communicate currently, they need to be on the
same Podman Network. Then each of them will be available by the name in the
Deployment or Pod .metadata.name key.I believe Podman attempts to tack on a
`-0` at the end to make the Pods unique.
