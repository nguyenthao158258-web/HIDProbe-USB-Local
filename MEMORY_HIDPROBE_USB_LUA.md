# MEMORY HIDProbe USB Local + Lua

File nay de nguoi khac/Codex khac doc va hieu cach cai, ket noi, viet Lua cho HIDProbe.

## Tai file cai dat

- IPA: `https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbeApp_AGENT_LAUNCHDAEMON_USB_20260630_1903.ipa`
- ZIP installer agent: `https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/HIDProbe_AGENT_LAUNCHDAEMON_USB_20260630_1903.zip`
- DEB rootless: `https://raw.githubusercontent.com/nguyenthao158258-web/HIDProbe-USB-Local/main/dist/hidprobe-agent_1.0.0_iphoneos-arm64.deb`

## Kien truc

- iPhone cai IPA bang TrollStore.
- `hidprobe_agent` chay nen bang LaunchDaemon `com.hidprobe.agent`.
- Agent listen port `17391`.
- PC/Mac ket noi iPhone qua USB port forward den `127.0.0.1:17391`.
- OCR/findText nen xu ly ben PC; agent nhan tap/swipe/screenshot.
- Khong dung WDA lam huong chinh.

## Kiem tra tren iPhone

```bash
launchctl list | grep hidprobe
ps aux | grep hidprobe_agent
tail -n 80 /var/mobile/Library/Logs/hidprobe-agent.log
cat /var/mobile/Library/Logs/hidprobe-agent-heartbeat.json
```

## Kiem tra tren PC/Mac sau khi USB forward

```bash
curl http://127.0.0.1:17391/health
curl -o screen.jpg http://127.0.0.1:17391/screenshot.jpg
```

## Cai agent qua SSH neu IPA khong tu load duoc

Giai nen ZIP installer roi chay:

```bash
bash install_hidprobe_agent_ssh.sh root@IPHONE_IP
```

Neu SSH port khac:

```bash
bash install_hidprobe_agent_ssh.sh root@IPHONE_IP 2222
```

## Lua: toa do

Lua dung toa do chuan hoa:

- `x = 0.0` trai, `x = 1.0` phai.
- `y = 0.0` tren, `y = 1.0` duoi.
- Tam man hinh: `tap(0.5, 0.5)`.

## Lua: ham hay dung

```lua
tap(x, y)
longPress(x, y, holdMs)
swipe(x1, y1, x2, y2, durationMs, steps)
home()
openApp("bundle.id")
killApp("bundle.id")
sleep(ms)
wait(seconds)
toast("noi dung")
reportStep("noi dung")
inputText("abc")
deleteText(count)
getScreenSize()
getBatteryLevel()
getColor(x, y)
findColor(colorHex, tolerance)
waitForColor(colorHex, tolerance, timeoutMs)
findText("text")
tapText("text")
waitForText("text", timeoutMs)
element.tap({ text = "OK" })
```

## Mau Lua tap OK moi 5 phut

```lua
reportStep("ok_loop:start")

while true do
  tap(0.5, 0.603)
  reportStep("ok_loop:tapped")
  sleep(300000)
end
```

## Mau Lua dem nguoc 05:00

```lua
local interval = 300

while true do
  tap(0.5, 0.603)
  reportStep("ok:tapped")

  for remain = interval, 1, -1 do
    local m = math.floor(remain / 60)
    local s = remain % 60
    toast(string.format("OK con %02d:%02d", m, s), 900)
    sleep(1000)
  end
end
```

## Luu y

- Agent nen van song khi app HID dong neu LaunchDaemon da load.
- Lua engine day du hien van nam trong app HID IPA. Muon Lua van chay khi app dong thi can dua Lua runner vao agent o ban tiep theo.
- Khong public source code, token, API key len repo nay.
