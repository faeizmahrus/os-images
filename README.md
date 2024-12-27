# os-images &nbsp; [![bluebuild build badge](https://github.com/faeizmahrus/os-images/actions/workflows/build.yml/badge.svg)](https://github.com/faeizmahrus/os-images/actions/workflows/build.yml)

My personal OCI container images.

Instructions for ISO generation: [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso).

Verify the image signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/faeizmahrus/kinoite-mahrus
```
### <b> For distrobox images: [distrobox-images-boxkit](https://github.com/faeizmahrus/distrobox-images-boxkit)

## Image list
- ### [kinoite-mahrus](recipes/kinoite-mahrus.yml) <br>
  Fedora Kinoite image with the RPMFusion repos, Brave Browser, entire Noto font family, OpenBangla Keyboard and many other things preinstalled.
- ### [silverblue-mahrus](recipes/kinoite-mahrus.yml) <br>
  Fedora Silverblue image with the RPMFusion repos, Brave Browser, entire Noto font family, OpenBangla Keyboard and many other things preinstalled.
  
## Installing kinoite-mahrus
To rebase an existing atomic Fedora installation to the latest build:

- First, rebase to the unsigned image to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/faeizmahrus/kinoite-mahrus:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Finally, rebase to the signed image:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/faeizmahrus/kinoite-mahrus:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build.

## BlueBuild
See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.
