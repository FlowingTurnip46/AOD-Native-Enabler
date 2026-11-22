# One UI 9 Native AOD Enabler for Galaxy A17 4G

A KernelSU module that enables Samsung's native Always On Display service on the Samsung Galaxy A17 4G (SM-A175F).

This project is an adaptation of Raphael Solis's original Galaxy A16 module, with device-specific compatibility changes and fixes developed for the Galaxy A17 4G.

«Status: Experimental, confirmed working on the maintainer's Galaxy A17 4G.»

✨ Features

- Enables Samsung's native Always On Display service.
- Systemless installation through KernelSU.
- Preserves the original Samsung ClockPack app.
- Fixes the conflicting ClockPack floating-feature configuration.
- Includes device-specific privileged permission configuration.
- Checks device model, firmware fingerprint and AOD APK integrity.
- Automatically prevents mounting on unverified firmware builds.

📱 Compatibility

Component| Configuration
Device| Samsung Galaxy A17 4G
Model| SM-A175F
Android| Android 17
One UI| One UI 9
Root manager| KernelSU
Verified firmware| A175FXXU7DZJ3_OXM7DZJ5
AOD service version| 8.9.36.23

Important: Compatibility with other firmware versions, the A17 5G, or other Samsung devices has not been established.

📋 Requirements

- Samsung Galaxy A17 4G (SM-A175F).
- Verified One UI 9 firmware listed above.
- KernelSU installed and functioning.
- Stock Samsung ClockPack app installed and enabled.

🚀 Installation

1. Download the latest ZIP from the "Releases" (../../releases) section.
2. Open KernelSU.
3. Install the downloaded ZIP as a module.
4. Reboot your device.
5. Open your Always On Display settings.

Do not disable or uninstall Samsung ClockPack. The module relies on the stock app remaining installed and enabled.

⚙️ Technical Details

The module installs Samsung's native AOD service through a systemless KernelSU overlay.

The A17 adaptation includes:

- Device-specific installer checks.
- Privileged permission configuration.
- AOD feature configuration.
- A floating-feature compatibility fix.

The fix clears the conflicting "SEC_FLOATING_FEATURE_FRAMEWORK_CONFIG_CLOCKPACK_ITEM" value while preserving the AOD configuration ("aodversion=7").

This allows Samsung's AOD service to initialize in AOD mode without removing the stock ClockPack application.

🛠️ Troubleshooting

If AOD does not appear or the service crashes:

1. Verify that your firmware matches the supported build.
2. Make sure Samsung ClockPack is installed and enabled.
3. Check KernelSU's installation report.
4. Check for conflicts with other AOD-related modules.
5. Use the included "collect-test-logs.sh" script to collect diagnostic information.

Avoid manually modifying system files or deleting AOD application data as an initial troubleshooting step.

👥 Credits & Contributors

- Raphael Solis: Original Galaxy A16 One UI 9 Native AOD module and implementation.
- qzeeq: Galaxy A17 4G compatibility work, installer modifications, permission configuration, floating-feature fix, testing and documentation.
- Samsung: Original AOD and ClockPack software.

⚠️ Disclaimer

This is an unofficial community project. It is not affiliated with, endorsed by, or supported by Samsung.

This module is experimental and provided without warranty. Root modifications can cause system instability or boot issues. Always keep a backup and a recovery method available.

📜 Licensing

This project is derived from Raphael Solis's original A16 implementation. Please consult the original repository's licence and obtain permission where required before redistributing modified versions.

Samsung's proprietary applications and components remain the property of Samsung. This project does not claim ownership of them.
