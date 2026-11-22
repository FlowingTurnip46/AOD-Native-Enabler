# Troubleshooting

## 1. AOD Does Not Appear

Check the following:

- The device is running the verified firmware.
- Samsung ClockPack is installed.
- ClockPack is enabled.
- The module is enabled in KernelSU.
- No other module conflicts with Samsung AOD components.

Reboot after making module changes.

## 2. Installation Aborts

The installer performs strict compatibility checks.

Common reasons include:

| Message | Explanation |
|---|---|
| Unsupported model | The device is not SM-A175F |
| Firmware not verified | The build fingerprint is not in the allowlist |
| ClockPack missing | The original ClockPack package is unavailable |
| ClockPack disabled | The original app is disabled |
| AOD APK mismatch | The bundled APK failed SHA-256 verification |
| Permission audit mismatch | The permission audit does not match the expected firmware |

Do not bypass installer checks to force installation.

## 3. Module Disables Itself After an Update

The module checks the firmware fingerprint during boot.

A firmware update can change this fingerprint.

The module disables its mount when it detects an unverified build.

Wait for compatibility verification and a new release rather than bypassing the protection.

## 4. Collecting Diagnostic Logs

The module includes:

`collect-test-logs.sh`

Run it from a root shell:

`su -c sh /data/adb/modules/a17_native_aod_coexist/collect-test-logs.sh`

The script collects diagnostic information for troubleshooting.

The module also performs one diagnostic collection after Android finishes booting.

Review the generated output before sharing it publicly. Diagnostic logs may contain device identifiers and other private information.

## 5. Reporting Issues

First of, keep in mind that the only Samsung device i own is the A17 4G so if you have any issues with a different model, i will probably not be able to help much without physical access to your device(or remotely)
When opening a GitHub issue, include:

- Device model
- Android and One UI versions
- Firmware build
- KernelSU version
- Installation report
- Relevant diagnostic output
- A description of the issue and steps to reproduce it

Remove personal information from logs before uploading them.

## 6. Recovery

If the module causes problems:

1. Enter a recovery environment or use KernelSU's available module management options.
2. Disable or remove the A17 Native AOD module.
3. Reboot.
4. Verify that the device starts normally.

Do not manually delete unrelated Samsung system applications or modify system partitions.
