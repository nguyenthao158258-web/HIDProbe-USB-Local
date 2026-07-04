# HIDProbe USB Local

Trang nay chi public file cai dat de cai tren iPhone jailbreak/TrollStore.

Khong public source code. Khong public app dieu khien may tinh.

## Tai IPA ngay

👉 [Bam vao day de tai IPA](https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_HIDPROBE_AGENT_DAEMON_20260704_2342.ipa)

Ten file: `HIDProbeApp_HIDPROBE_AGENT_DAEMON_20260704_2342.ipa`

Ban nay chuyen port `17391` sang daemon rieng `HIDProbeAgent` chay bang LaunchDaemon `com.hidprobe.agent`. App HID mac dinh khong mo local server 17391 nua, chi la setup/config/status. `HIDProbeAgent` listen `0.0.0.0:17391`, xu ly HPB1 Health/Frame/Hid/Ack/Script, stream frame JPEG, tap/swipe/key/text va Lua co ban trong daemon.

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

SHA256 IPA: `49cc03f0d20c1aa2c3a6cc787fd2b4541f6a8592c2edb1ae9273c36236274383`

## Ghi chu

- Cai IPA bang TrollStore tren iPhone.
- Sau khi cai, kiem tra: `launchctl list | grep hidprobe`.
