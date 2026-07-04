# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_TEMPLATE_ONLY_POINT_20260704_1953.ipa)

Ten file: `HIDProbeApp_TEMPLATE_ONLY_POINT_20260704_1953.ipa`

Ban nay bo OCR tieng Han `ko-KR` va uu tien template matching cho nut `포인트 받기`. IPA co san template `point_receive_ko_button_template.png`; test thuc te qua Lua tren iPhone da tim dung nut voi score khoang `0.982` va tap dung nut.

Van giu `hidprobe_agent` chay nen bang LaunchDaemon:

- Agent nen listen port USB/native `17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/mobile/Library/Logs/hidprobe-agent.log`.
- Co heartbeat: `/var/mobile/Library/Logs/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `00a863b5690d8be865d202981fcf50e645e4c3534454abf141952af92bbaa522`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
