# Upstream protocol baseline

This document records the Phase 0 KDE Connect compatibility baseline for the Android and desktop clients. It is descriptive only and does not redefine the protocol.

## Baseline

- Android upstream: `KDE/kdeconnect-android`
- Desktop upstream: `KDE/kdeconnect-kde`
- Protocol version: 8 on both clients.
- Core packet types: `kdeconnect.identity` and `kdeconnect.pair`.

## Core implementation paths

Android:
- `DeviceInfo.kt`, `Device.kt`, `PairingHandler.kt`, `NetworkPacket.kt`
- `backends/lan/`, `backends/bluetooth/`
- `Plugin.kt`, `PluginFactory.kt`

Desktop:
- `core/device.*`, `core/backends/pairinghandler.*`, `core/networkpacket.*`
- `core/backends/lan/`, `core/backends/bluetooth/`
- `core/pluginloader.*`, `core/kdeconnectplugin.*`

## Packet compatibility inventory

Verified packet families present on both sides include battery, clipboard, connectivity report, contacts, digitizer, find-my-phone, mouse/keyboard input, MPRIS, notifications, ping, presenter, run-command, SFTP, share/file transfer, shared-input-devices, SMS, system volume, and telephony.

Representative shared identifiers:
- `kdeconnect.battery`
- `kdeconnect.clipboard`
- `kdeconnect.clipboard.connect`
- `kdeconnect.mpris`
- `kdeconnect.mpris.request`
- `kdeconnect.notification`
- `kdeconnect.notification.request`
- `kdeconnect.notification.reply`
- `kdeconnect.notification.action`
- `kdeconnect.mousepad.request`
- `kdeconnect.mousepad.keyboardstate`
- `kdeconnect.mousepad.echo`
- `kdeconnect.runcommand`
- `kdeconnect.runcommand.request`
- `kdeconnect.runcommand.output`
- `kdeconnect.sftp`
- `kdeconnect.sftp.request`
- `kdeconnect.share.request`
- `kdeconnect.share.request.update`
- `kdeconnect.shareinputdevices`
- `kdeconnect.shareinputdevices.request`
- `kdeconnect.systemvolume`
- `kdeconnect.systemvolume.request`
- `kdeconnect.telephony`
- `kdeconnect.telephony.request_mute`

At the Phase 0 baseline, desktop also advertises packet types not found in Android source:
- `kdeconnect.clipboard.file`
- `kdeconnect.lock`
- `kdeconnect.lock.request`
- `kdeconnect.virtualmonitor`
- `kdeconnect.virtualmonitor.request`

No packet identifier in this inventory was clearly marked upstream as deprecated.

## Compatibility rule

Future product work should preserve protocol version handling, identity/certificate semantics, pairing, capability advertisement, packet identifiers, and plugin negotiation unless a deliberate protocol change is separately designed and tested.
