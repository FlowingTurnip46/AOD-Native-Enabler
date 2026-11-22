# Technical Documentation

## 1. Architecture

The A17 Native AOD Enabler is a KernelSU module that installs Samsung's native AOD service through a systemless overlay.

It does not intentionally modify the original read-only system partition.

### Main Components

| Component | Purpose |
|---|---|
| `customize.sh` | Installation checks and configuration |
| `post-fs-data.sh` | Firmware fingerprint verification |
| `service.sh` | Post-boot diagnostic collection |
| `uninstall.sh` | Removes module-owned diagnostic data |
| `module.prop` | KernelSU module metadata |
| `collect-test-logs.sh` | Collects diagnostic information |

## 2. Samsung AOD Service

The module installs the Samsung AOD application:

- Package: `com.samsung.android.app.aodservice`
- Version: `8.9.36.23`
- Target SDK: 36

The APK is installed under:

`/system/priv-app/SamsungAODCoexist/`

The application requires appropriate Samsung platform integration, including privileged permissions and package configuration.

## 3. Floating Feature Configuration

Samsung uses `floating_feature.xml` to configure device-specific software capabilities.

Two important entries are involved:

### AOD Item

`SEC_FLOATING_FEATURE_FRAMEWORK_CONFIG_AOD_ITEM`

The verified device configuration uses:

`aodversion=7`

### ClockPack Item

`SEC_FLOATING_FEATURE_FRAMEWORK_CONFIG_CLOCKPACK_ITEM`

The original A17 configuration contains:

`clockpackversion=7`

This value causes the AOD service to enter ClockPack mode, which skips creation of the AOD settings database table.

The A17 adaptation clears this conflicting value in a systemless overlay while preserving the AOD configuration.

**The ClockPack application itself remains installed and enabled.**

## 4. Privileged Permissions

The AOD APK requests 89 permissions.

The firmware-specific audit identified:

- 2,752 permission definitions on the verified firmware.
- 70 requested permissions defined by the system.
- 43 requested privileged permissions.

The module includes a privileged-permission configuration containing the 43 verified entries.

The installer checks the permission audit and associated file hashes before proceeding.

## 5. Firmware Protection

The module is pinned to an explicitly verified firmware fingerprint.

During installation, the installer checks:

- Device model
- One UI version
- Android SDK level
- Firmware fingerprint
- ClockPack installation and enabled state
- AOD APK SHA-256
- System UI shared UID and signing information
- Privileged permission audit integrity

During boot, `post-fs-data.sh` checks the firmware fingerprint again.

If the fingerprint is not recognized, the module disables its mount until the firmware has been re-verified.

Do not bypass this protection.

## 6. Systemless Design

The module uses KernelSU's module overlay mechanism.

Its generated floating-feature configuration is based on the device's own system XML rather than a replacement file copied from another device.

This reduces the risk of overwriting unrelated device-specific configuration.

## 7. Limitations

- Only the Galaxy A17 4G SM-A175F is verified.
- Only the explicitly listed firmware fingerprint is verified.
- Other Samsung firmware builds may have different permission definitions or package integration.
- Samsung AOD and ClockPack components remain proprietary software.
