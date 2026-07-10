# HIDProbe USB Local

Repo nay chi public file cai dat IPA de cai tren iPhone TrollStore/no-jailbreak style.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA moi nhat

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_TROLLSTORE_USB_LOCAL_HARD_UPGRADE_20260710_174849.ipa)

Ten file: `HIDProbeApp_TROLLSTORE_USB_LOCAL_HARD_UPGRADE_20260710_174849.ipa`

SHA256 IPA: `cc40876970a4fb31d46feec5d7bfe7ec783af2d5b07b08b847563a23d6fa3271`

## Ban nay sua gi

- Day la line IPA TrollStore/no-jailbreak app-local USB.
- App HID tu mo USB Local server port `17391` mac dinh.
- Khong mac dinh chuyen port `17391` sang `HIDProbeAgent` external LaunchDaemon nua.
- `hidprobe_daemon` chi giu vai tro watchdog: neu iOS kill HIDProbeApp thi daemon goi SpringBoard/FrontBoard de mo lai app.
- Khi app moi mo len, installer daemon se hard-upgrade: bootout/kill daemon cu, xoa file HIDProbe-owned cu, copy lai `hidprobe_daemon` va `com.local.hidprobe.daemon.plist` moi.
- Build moi da bump `CFBundleVersion=20260710174849`, tranh tinh trang cai IPA moi nhung iOS/TrollStore van nhin nhu ban cu.
- `hidprobe_daemon` trong IPA da duoc ky bang entitlement rieng cua daemon, co:
  - `com.apple.frontboard.launchapplications`
  - `com.apple.springboard.launchapplications`
  - `com.apple.runningboard.launchprocess`
  - `platform-application`
  - `no-sandbox` / `no-container`

## Duong dan runtime tren iPhone

- App bundle ID: `com.local.hidprobe`
- USB Local app server: port `17391`
- Daemon binary TrollStore/no-JB: `/var/mobile/Documents/hidprobe_daemon`
- Daemon plist TrollStore/no-JB: `/var/mobile/Library/LaunchDaemons/com.local.hidprobe.daemon.plist`
- Daemon heartbeat: `/var/mobile/Documents/hidprobe_daemon_heartbeat.json`
- Daemon log: `/var/mobile/Documents/hidprobe_daemon.log`
- Daemon upgrade log: `/var/mobile/Documents/hidprobe_daemon_upgrade.log`

## Cach cai

1. Cai IPA bang TrollStore.
2. Mo HID Probe it nhat 1 lan de app copy/lap lai daemon.
3. Trong app, dong `USB Local:` phai hien server app dang chay, khong phai `daemon_mode`.
4. Neu vua cai de len ban cu, hay mo app moi nay mot lan de no hard-upgrade/xoa file daemon cu.

## Luu y

Ban `HIDPROBE_AGENT_EXTERNAL_DETECT_20260705_0903` cu dung line external agent rieng va co the lam app HID khong tu mo local server `17391`. Neu muc tieu la IPA no-jailbreak app-local USB thi dung ban moi nhat o tren.
