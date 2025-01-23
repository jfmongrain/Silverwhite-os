# Silverwhite &nbsp; [![bluebuild build badge](https://github.com/jfmongrain/silverwhite-os/actions/workflows/build.yml/badge.svg)](https://github.com/jfmongrain/silverwhite-os/actions/workflows/build.yml)

Silverwhite 
===============
This is a custom image based on Ublue-main, created for my personnal use so I do not have layer or remove packages. It is not intended to be used by other people. 

Seriously don't do it. You have been warned.

See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/jfmongrain/silverwhite-os:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/jfmongrain/silverwhite-os:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/jfmongrain/silverwhite-os
```

https://github.com/ublue-os
