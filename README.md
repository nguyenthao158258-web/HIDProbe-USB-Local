# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_SEPARATE_STOP_BUTTONS_20260704_2235.ipa)

Ten file: `HIDProbeApp_SEPARATE_STOP_BUTTONS_20260704_2235.ipa`

Ban nay tach rieng nut dung cua `Get Han` va `Lua OK tu dong`: khi `Get Han` dang chay thi chi hien `Dung Get Han`, khi OK dang chay thi chi hien `Dung OK`. Van giu bang `Get Han` rieng trong tab Local: bam `Chay Get Han` thi doi 3 phut roi get lan 1, sau do chay tong 10 luot, moi luot cach nhau 22 phut. Nut `포인트 받기` duoc tim bang template `point_receive_ko_button_template.png`, khong dung OCR tieng Han.

Van giu `hidprobe_agent` chay nen bang LaunchDaemon:

- Agent nen listen port USB/native `17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/mobile/Library/Logs/hidprobe-agent.log`.
- Co heartbeat: `/var/mobile/Library/Logs/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `921f51765ec9028d3efbc4358144cb48baea15af7c929516956420e4f61ff4bb`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
