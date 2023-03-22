# darwin-plymouth

This an awesome, sophisticated and minimalist Plymouth Theme.

## Prerequisites

In order to use this theme, you need to install and configure Plymouth application to show a graphical boot animation while the boot process happens in the background. To achieve this run these commands:

```bash
$ sudo apt install plymouth plymouth-themes
```

And configure Plymouth for your graphic card, editing the file `/etc/initramfs-tools/modules` and adding these modesetting lines:

* **For Intel Graphic Cards:**
    ```ini
    # KMS
    intel_agp
    drm
    i915 modeset=1
    ```
* **For NVidia Graphic Cards:**
    ```ini
    # KMS
    drm
    nouveau modeset=1
    ```
* **For ATI Graphic Cards:**
    ```ini
    # KMS
    drm
    radeon modeset=1
    ```

## How to install it?

Follow this instructions from a Terminal:

1. Copy `darwin` folder to path `/usr/share/plymouth/themes/`:
    ```bash
    $ sudo cp -R darwin/ /usr/share/plymouth/themes/
    ```

2. Install it running these commands:
    ```bash
    $ sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/darwin/darwin.plymouth 100

    $ sudo update-alternatives --config default.plymouth
    ```

    And choose the plymouth theme number, then press Enter key

3. Activate it running this command:
    ```bash
    $ sudo update-initramfs -u
    ```