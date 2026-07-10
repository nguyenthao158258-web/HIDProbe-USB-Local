# HIDProbe USB Local

Repo nay chi public file cai dat IPA de cai tren iPhone TrollStore/no-jailbreak style.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA moi nhat

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_DOPAMINE_PERSONA_COMPATIBLE_20260710201500.ipa)

Ten file: `HIDProbeApp_DOPAMINE_PERSONA_COMPATIBLE_20260710201500.ipa`

SHA256 IPA: `22b05d014e39996a19e23247609de82d7011c368ad3fa156a10662cec5718153`

## Ban nay sua gi

- Day la line IPA TrollStore/no-jailbreak app-local USB.
- App HID tu mo USB Local server port `17391` mac dinh.
- Khong mac dinh chuyen port `17391` sang `HIDProbeAgent` external LaunchDaemon nua.
- `hidprobe_daemon` chi giu vai tro watchdog: neu iOS kill HIDProbeApp thi daemon goi SpringBoard/FrontBoard de mo lai app.
- Khi app moi mo len, installer daemon se hard-upgrade: bootout/kill daemon cu, xoa file HIDProbe-owned cu, copy lai `hidprobe_daemon` va `com.local.hidprobe.daemon.plist` moi.
- Ban nay sua loi sau reboot: no-JB path ghi plist vao `/var/mobile/Library/LaunchAgents` truoc, thay vi chi ghi `/var/mobile/Library/LaunchDaemons`.
- Neu `launchctl bootstrap gui/501` bi iOS 15 tu choi, installer thu tiep `launchctl load -w` va `launchctl bootstrap user/501`.
- Installer dat ownership cua plist/binary theo user mobile cho layout `gui/501`, thay vi ep root ownership.
- Upgrade log ghi them uid/euid/gid/egid, owner/mode/size cua plist va binary, `manageruid`, `managername`, `launchctl error 85`, va ket qua tung lenh load.
- Ban Dopamine recovery dung root persona helper de copy plist vao `/var/jb/Library/LaunchDaemons`, dat owner root va mode 0644. Muc dich la de Dopamine launchd hook mo watchdog va HID ngay sau khi Dopamine duoc kich hoat.
- Build nay da bo entitlement `com.apple.private.persona-mgmt` lam TrollStore bao `0xe8008014`, nhung van giu root-persona spawn tren nen `platform-application` va `no-sandbox`.
- Installer ghi marker build sau khi copy plist/bin thanh cong, tranh viec moi lan mo app lai kill/copy daemon lap lai.
- Upgrade log co them exit code `launchctl_bootstrap` de doc loi neu iOS van chan bootstrap.
- Build moi da bump `CFBundleVersion=20260710201500`, tranh tinh trang cai IPA moi nhung iOS/TrollStore van nhin nhu ban cu.
- Daemon version: `hidprobe_daemon/1.3.9-persona-compatible`.
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
- Daemon plist TrollStore/no-JB uu tien: `/var/mobile/Library/LaunchAgents/com.local.hidprobe.daemon.plist`
- Daemon plist cu se duoc clean neu co: `/var/mobile/Library/LaunchDaemons/com.local.hidprobe.daemon.plist`
- Daemon heartbeat: `/var/mobile/Documents/hidprobe_daemon_heartbeat.json`
- Daemon log: `/var/mobile/Documents/hidprobe_daemon.log`
- Daemon upgrade log: `/var/mobile/Documents/hidprobe_daemon_upgrade.log`

## Cach cai

1. Cai IPA bang TrollStore.
2. Mo HID Probe it nhat 1 lan de app copy/lap lai daemon.
   - Voi ban Dopamine recovery: mo HID Probe mot lan de app stage LaunchDaemon vao `/var/jb`.
   - Kiem tra upgrade log co `rootless_stage success=true` truoc khi reboot.
3. Trong app, dong `USB Local:` phai hien server app dang chay, khong phai `daemon_mode`.
4. Tat nguon/bat lai iPhone de test reboot. Sau khi may len, doi khoang 30-60 giay roi kiem tra `/var/mobile/Documents/hidprobe_daemon_heartbeat.json`.
5. Truoc khi reboot, doc `/var/mobile/Documents/hidprobe_daemon_upgrade.log`. Can tim mot trong ba dong co `exit=0`: `launchctl_bootstrap`, `launchctl_load`, hoac `launchctl_bootstrap_user`.
6. Neu ca ba deu khong co `exit=0`, iOS da chan user launchd domain; ket qua do xac nhan IPA khong the tu dang ky cold-boot watchdog chi bang quyen app.

## Luu y

Ban `HIDPROBE_AGENT_EXTERNAL_DETECT_20260705_0903` cu dung line external agent rieng va co the lam app HID khong tu mo local server `17391`. Neu muc tieu la IPA no-jailbreak app-local USB thi dung ban moi nhat o tren.
