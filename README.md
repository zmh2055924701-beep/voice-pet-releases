# Voice Pet Firmware Releases

This repository hosts signed firmware for the Voice Pet device.

- The device only installs firmware signed by the matching offline ECDSA P-256 key.
- `manifest.json` points devices to the latest signed firmware.
- No Wi-Fi passwords, API keys, personal memories, or source code are stored here.
- Firmware is downloaded over HTTPS and verified on-device before activation.
- A failed download or invalid signature leaves the currently running firmware intact.

Current release: `1.9.1`

## Device update flow

1. The owner opens Settings and selects the cloud update item.
2. The device connects to its saved Wi-Fi and reads `manifest.json`.
3. If the manifest version is newer, the device downloads the signed firmware into
   its inactive OTA partition.
4. The embedded public key verifies the ECDSA P-256 SHA-256 signature.
5. Only a successfully verified image is activated and rebooted.

## Published files

- `manifest.json`: latest version, signed firmware URL, size, and audit SHA-256.
- `firmware/voice-pet-<version>-signed.bin`: installable signed application image.

The private signing key is never stored in this repository.
