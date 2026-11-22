# Installation Guide

## 1. Overview

This guide explains how to install, update and remove the One UI 9 Native AOD Enabler on the Samsung Galaxy A17 4G.

The module is installed through KernelSU and uses a systemless overlay.

## 2. Requirements

Before installing, make sure you have:

- Samsung Galaxy A17 4G (SM-A175F)
- Android 17
- One UI 9
- The verified firmware build
- Working KernelSU installation
- Original Samsung ClockPack application installed and enabled

The module is not verified for other device variants or firmware versions.

## 3. Installation

1. Download the latest compatible module ZIP from GitHub Releases.
2. Open KernelSU.
3. Navigate to the Modules section.
4. Select Install from storage.
5. Choose the downloaded ZIP.
6. Wait for the installer to complete.
7. Reboot your device.

After rebooting, open your device's Always On Display settings.

## 4. Important Notes

**Do not disable or uninstall Samsung ClockPack.**

The module preserves the original ClockPack application and changes the floating-feature configuration needed for native AOD operation.

Do not install multiple AOD modules simultaneously if they modify the same Samsung packages or floating-feature configuration.

## 5. Updating

1. Download the new release.
2. Check its compatibility information.
3. Remove the previous module through KernelSU if the release instructions require it.
4. Reboot.
5. Install the new ZIP.
6. Reboot again.

Never manually overwrite files inside the active module directory.

## 6. Uninstallation

1. Open KernelSU.
2. Navigate to Modules.
3. Select the A17 Native AOD module.
4. Remove it.
5. Reboot.

The module's systemless overlay will no longer be applied after removal.

The stock ClockPack application is not removed by this module.
