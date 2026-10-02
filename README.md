# Rob2 Operator

Drive **Rob2** (4 omni wheels) with a game controller, from any device with a browser.

**Open:** https://louisproy456.github.io/rob2-operator/

```
Controller --> this web page --> EMQX Cloud (wss 8084) --> tablet "final1" --> USB --> ESP32-S3
```

## Status

| Step | What | State |
|---|---|---|
| 0 | Page online on GitHub Pages, device check | REV 0.1 |
| 1 | Controller test + Learn wizard + sticks preview | REV 0.1 |
| 2 | Connect to EMQX (settings, ping, robot status) | next |
| 3 | Drive Rob2 (same table as `robot_operator.py --sticks`) | later |
| 4 | Safety tests | later |
| 5 | Other devices + student guide | later |

## Which controller works where

| Device | Logitech F310 (USB) | Xbox / PlayStation |
|---|---|---|
| MacBook, Chrome | yes, switch on the back = **D** | yes |
| Windows, Chrome or Edge | yes (X or D) | yes |
| Linux, Chrome | yes | yes |
| Android phone or tablet, Chrome (USB-C adapter) | very likely | yes |
| iPad / iPhone (any browser) | probably not | yes (Bluetooth or USB-C) |

## Controls (Step 3, same as `--sticks`)

| Do this | Motion |
|---|---|
| Left stick UP / DOWN / LEFT / RIGHT | forward / backward / strafe left / strafe right |
| Stick UP + X, UP + B | diagonal forward-left / forward-right |
| Stick DOWN + X, DOWN + B | diagonal back-left / back-right |
| Stick LEFT + Y, RIGHT + Y | rotate left / rotate right |
| Let go of the stick | STOP |
| D-pad UP / DOWN | speed 25 / 50 / 75 / 100 % |
| Hold A | 100 % while held |
| LB + RB + START | STOP ALL |

## Files

| File | Purpose |
|---|---|
| `index.html` | the page (all the code, with comments) |
| `mqtt.min.js` | MQTT.js 5.16.0 browser build (MIT licence, see `MQTT-LICENSE.md`) |
| `manifest.json`, `icon-192.png`, `icon-512.png` | "Add to Home Screen" app icon |

**No password is stored in this repository.** The EMQX password is typed once on each
device (Step 2) and stays on that device.
