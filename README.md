# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_OCR_KOREAN_20260704_181503.ipa)

Ten file: `HIDProbeApp_OCR_KOREAN_20260704_181503.ipa`

Ban nay them OCR tieng Han `ko-KR` cho `tapText/findText` va giu `hidprobe_agent` chay nen bang LaunchDaemon:

- Agent nen listen port USB/native `17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/mobile/Library/Logs/hidprobe-agent.log`.
- Co heartbeat: `/var/mobile/Library/Logs/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `ac952db02e5a111b0c1d297d3802711522b5ea3a4759527ae7992336b1bfebd3`

## Tai goi installer agent

Neu IPA khong du quyen tu ghi LaunchDaemon, tai goi nay de cai qua SSH hoac DEB:

👉 [Bam vao day de tai ZIP installer](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbe_AGENT_LAUNCHDAEMON_USB_20260630_1903.zip)

SHA256 ZIP: `cbb6d4f47008170b306110c4330588d2316653205d8327627a04d1e371d61935`

👉 [Bam vao day de tai DEB rootless](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/hidprobe-agent_1.0.0_iphoneos-arm64.deb)

SHA256 DEB: `71db2973932c481b179b523b6d400a575990bcf685b5099fbb80e2940717e447`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Neu agent chua load, dung file `install_hidprobe_agent_ssh.sh` trong ZIP de cai qua SSH.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
