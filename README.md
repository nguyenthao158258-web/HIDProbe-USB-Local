# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_TEMPLATE_MATCH_KOREAN_POINT_20260704_1918.ipa)

Ten file: `HIDProbeApp_TEMPLATE_MATCH_KOREAN_POINT_20260704_1918.ipa`

Ban nay uu tien template matching cho nut tieng Han `포인트 받기`, de tap dung nut khi Apple Vision OCR tren iOS 15 khong support `ko-KR`. Test thuc te qua Lua tren iPhone: template match score khoang `0.982`, toa do tam nut khoang `x=0.7673 y=0.4022`.

Van giu `hidprobe_agent` chay nen bang LaunchDaemon:

- Agent nen listen port USB/native `17391`.
- App HID chi la setup/config/status.
- Dong app HID, ve Home, reset data app: agent van co the song neu LaunchDaemon da load.
- Ho tro rootless `/var/jb` va rootful.
- Co log: `/var/mobile/Library/Logs/hidprobe-agent.log`.
- Co heartbeat: `/var/mobile/Library/Logs/hidprobe-agent-heartbeat.json`.

SHA256 IPA: `5f38a508b8fc9123444ec9fd671c38ed93e9e2d1ea7701a513359859f1ac9a97`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
