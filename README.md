# Silverwhite-os &nbsp; [![bluebuild build badge](https://github.com/jfmongrain/silverwhite-os/actions/workflows/build.yml/badge.svg)](https://github.com/jfmongrain/silverwhite-os/actions/workflows/build.yml)

*Use at your own risk - experimental project*

Silverwhite 
===============
- Silverwhite is minimal install of Gnome, a blank page upon which you install the apps and extensions you want.  Based on Fedora Silverblue.
- The intended usage is as a boring desktop for the average person.  It is not a powertool for devs (check out Bluefin), nor a hobby distribution you can tweak for hours (but you can run Arch in a distrobox, by the way).
- Includes RPM Fusion codecs, some thumnailers, openssl, and french and english localisation.
- All apps that can be removed are removed.
  - No browser, no office suite, no text editor, no mail client, no extensions, no gnome-classic session, no theming.
  - You get the Gnome Software app, a terminal, a file manager, a disk manager and a system monitor, and you install everything else by yourself from Flathub.
  - Repos other than Flathub are removed by default.
  - Layering is disabled.
  - No Nvidia proprietary driver support.
  - Good old bash shell without any bling.  You get Fastfetch, but that's about it.
- Distrobox is included for other software needs.
- Updates are scheduled and done in the background.  This image updates twice a day.

*This was created for personnal use so I do not have to use rpm-ostree to layer or remove packages.  It is not intended to be used by other people.  You have been warned.*

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
