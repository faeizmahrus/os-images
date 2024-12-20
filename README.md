# os-images &nbsp; [![bluebuild build badge](https://github.com/faeizmahrus/os-images/actions/workflows/build.yml/badge.svg)](https://github.com/faeizmahrus/os-images/actions/workflows/build.yml)

My personal OCI container images.

## Image list
- ### [kinoite-mahrus](recipes/kinoite-mahrus.yml) <br>
  Fedora Kinoite image with the RPMFusion repos, Brave Browser, entire Noto font family, OpenBangla Keyboard and many other things preinstalled.
- ### [devbox-arch](recipes/devbox-arch.yml) <br>
  Distrobox image with the C/C++ toolchain, Rust toolchain and VSCode preinstalled.
- ### [appbox-arch](recipes/appbox-arch.yml) <br>
  Distrobox image with Obsidian, Zotero, KeePassXC and LibreOffice preinstalled. Based on `ublue-toolbox` image.
- ### [winebox-fedora](recipes/winebox-fedora.yml) <br>
  Distrobox image with `winehq-staging` preinstalled from the official WineHQ repos for Fedora. Their builds are compiled with WoW64 support and don't pull 32-bit libs. Some useful scripts are also included.

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

## ISO

You can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso).

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/faeizmahrus/kinoite-mahrus
```

## BlueBuild
See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.