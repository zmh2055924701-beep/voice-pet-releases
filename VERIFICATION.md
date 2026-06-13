# Voice Pet 1.9.1 Verification

Verified on an ESP32-S3 Voice Pet development board on 2026-06-12.

## Build and release

- Source version: `1.9.1`
- Compiled application size: `2038224` bytes
- Signed firmware size: `2038736` bytes
- Published signed firmware SHA-256:
  `60e4c35ad854d7a89af00ab8922d34d7dbda3f5dec9d3aa06ac570c5c6783b47`
- Signature scheme: ECDSA P-256 SHA-256

## Public download verification

- The public manifest reported version `1.9.1` and size `2038736`.
- The firmware downloaded from the public raw GitHub URL matched the manifest size
  and SHA-256.

## Device OTA verification

The board started from firmware `1.9.0`, downloaded the published signed image, and
reported:

```text
Cloud OTA manifest: current=1.9.0 target=1.9.1 size=2038736
Cloud OTA progress: 100%
Cloud OTA installed and signature verified: 1.9.1
```

After the automatic reboot, a second cloud update check reported:

```text
Cloud OTA manifest: current=1.9.1 target=1.9.1 size=2038736
```

This proves that the signed image was accepted, activated, rebooted, and is now the
running firmware.

## Failure behavior

With the saved Wi-Fi unavailable, the board reported `WI-FI CONNECTION FAILED` and
continued running its offline features without modifying the active firmware.

## Voice Pet 1.9.2 touch mapping fix

Verified on the same ESP32-S3 development board on 2026-06-13.

- Source version: `1.9.2`
- Compiled application size: `2038087` bytes
- Signed firmware size: `2038752` bytes
- Published signed firmware SHA-256:
  `42c1aa6f441cb965c012532b635382fd20cdf31f81ad15510b9571ad648a80fe`
- The public firmware download matched the manifest size and SHA-256.

Physical touch verification after installing `1.9.2`:

```text
Left physical touch pad  -> T1 active
Right physical touch pad -> T2 active
```

This confirms that the left and right touch bindings are no longer reversed.
