# Installing EndeavourOS on a Mac with the T2 Chip

You will need:

- USB drive with at least 4GB
- A way to plug it into your Mac (USB-C isn't USB-A)
- A wired internet connection (i.e. USB-C to Enternet dongle) or Wi-Fi.

---

1. Follow the [Pre-installation](https://wiki.t2linux.org/guides/preinstall) steps to prepare your Mac for the installation.

2. Boot into the ISO and start the Calamares installer

    1. If you're not connected to the internet, connect to it now. Use included GUI config tool to connect to Wi-Fi.

    !!! Note "Issues with Wi-Fi"
        Some Wi-Fi cards may have issues. If your Wi-Fi tool (e.g., nmcli or wifi-menu) reports that there are no networks found, try reprobing the network card by running `sudo modprobe -r $(lsmod | grep 'brcmfmac' | awk '{print $1}') && sudo modprobe brcmfmac` in a Konsole window.

3. Start the Calamares installer

    2. On the "Welcome" window, choose...

        1. "Install community editions" if you want to install community edition.
        2. "Start the Installer" if you want to install normal edition.

    3. If you chose to install normal edition, choose "Online" or "Offline" depending on your needs.

4. Follow the installer until Partitions.

    1. Select "Manual partitioning."
    2. Select "/dev/nvme0n1p1" partition, make sure the "boot" flag is set, and set it to mount under "/efi". If you want to use separate EFI partition, check out [this guide](https://wiki.t2linux.org/guides/windows/#using-seperate-efi-partitions).
    3. Use remaining partition space to your convenience.

5. Follow the rest of the installer and reboot.

    !!! Note "Issue: `the package manager could not make changes to the installed system. The command <pre>pacman</pre> returned error code 1`"
        If you encounter this issues when installing, reboot, and in a Konsole window, run either `sudo cp /etc/calamares/settings_online.conf /etc/calamares/settings.conf` (For Online mode install) or `sudo cp /etc/calamares/settings_offline.conf /etc/calamares/settings.conf` (For Offline mode install), and then start the Calamares Installer.

6. You can follow the [Fan guide](https://wiki.t2linux.org/guides/fan/) after rebooting into your install if your fan isn't working or if you want to customize how/when your fan will run.

7. You now will be able to select your EndeavourOS install in the macOS Startup Manager by holding option at boot.

8. Optionally, enable `bluetooth` daemon if you want to use Bluetooth.
