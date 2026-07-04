# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_GET_HAN_CARD_20260704_2213.ipa)

Ten file: `HIDProbeApp_GET_HAN_CARD_20260704_2213.ipa`

Ban nay them bang `Get Han` rieng trong tab Local, tuong tu `Lua OK tu dong`. Bam `Chay Get Han` thi doi 3 phut roi get lan 1, sau do chay tong 10 luot, moi luot cach nhau 22 phut. Nut `포인트 받기` duoc tim bang template `point_receive_ko_button_template.png`, khong dung OCR tieng Han.

Van giu `hidprobe_agent` chay nen bang LaunchDaemon:

- Agent nen listen port USB/native `17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/mobile/Library/Logs/hidprobe-agent.log`.
- Co heartbeat: `/var/mobile/Library/Logs/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `c082523230807b4db0495c43afe87e5d8c27b7b19fcda47e45a5ee62cf1ff8ce`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
