# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_HIDPROBE_AGENT_SSH_READY_20260705_0859.ipa)

Ten file: `HIDProbeApp_HIDPROBE_AGENT_SSH_READY_20260705_0859.ipa`

Ban nay chuyen port `17391` sang daemon rieng `HIDProbeAgent` chay bang LaunchDaemon `com.hidprobe.agent`. App HID mac dinh khong mo local server 17391 nua, chi la setup/config/status. `HIDProbeAgent` listen `0.0.0.0:17391`, xu ly HPB1 Health/Frame/Hid/Ack/Script, stream frame JPEG, tap/swipe/key/text va Lua co ban trong daemon.

Ban SSH_READY nay bo fallback `gui/<uid>` cho agent chinh de khong bao nham thanh cong. Man hinh app co dong `Agent:` hien truc tiep `loaded port=17391 ...` hoac `failed ...`. Neu thay `no_writable_system_launchdaemon_layout` thi IPA khong du quyen tu ghi LaunchDaemon, can cai/load `HIDProbeAgent` bang SSH root hoac package jailbreak. Log installer de doc loi: `/var/mobile/Documents/hidprobe-agent-install.log`.

Script root cua agent la `/var/mobile/Documents`, de `store_script`, `run_script` va Lua `screenshot()` ghi file on dinh hon tren roothide.

Van giu bang `Get Han` rieng va nut dung tach rieng cua `Get Han` / `Lua OK tu dong`.

`HIDProbeAgent` LaunchDaemon:

- Binary: `/usr/local/bin/HIDProbeAgent` hoac rootless `/var/jb/usr/local/bin/HIDProbeAgent`.
- Plist: `/Library/LaunchDaemons/com.hidprobe.agent.plist` hoac rootless `/var/jb/Library/LaunchDaemons/com.hidprobe.agent.plist`.
- Agent nen listen IP/native `0.0.0.0:17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/log/hidprobe-agent.log`.
- Co heartbeat: `/var/log/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `4b793b6d8553e0404c1bcaee9fec1d95496bf4a073da3a154b6d1f28f8c5b162`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
