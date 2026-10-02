# Rob2 Operator

Drive **Rob2** (4 omni wheels) with a game controller, from any device with a browser.

**Open:** https://louisproy456.github.io/rob2-operator/

```
Controller --> this web page --> EMQX Cloud (wss 8084) --> tablet "final1" --> USB --> ESP32-S3
```

## Status

| Step | What | State |
|---|---|---|
| 0 | Page online on GitHub Pages, device check | done (REV 0.1) |
| 1 | Controller test + Learn wizard + sticks preview | done (REV 0.1) |
| 2 | Connect to EMQX (settings, ping, robot status) | done (REV 0.2) |
| 3 | Drive Rob2 (same table as `robot_operator.py --sticks`) | REV 0.3 |
| 4 | Safety tests | later |
| 5 | Other devices + student guide | later |

## Which controller works where

| Device | Logitech F310 (USB) | Xbox / PlayStation |
|---|---|---|
| MacBook, Chrome | yes, switch on the back = **D** | yes |
| Windows, Chrome or Edge | yes (X or D) | yes |
| Linux, Chrome | yes | yes |
| Android phone or tablet, Chrome (USB-C adapter) | very likely | yes |
| iPad / iPhone (any browser) | buttons work, sticks read wrong: use the **Buttons** control style | yes (Bluetooth or USB-C) |

## Controls — Sticks style (same as `--sticks`)

| Do this | Motion |
|---|---|
| Left stick UP / DOWN / LEFT / RIGHT | forward / backward / strafe left / strafe right |
| Stick UP + X, UP + B | diagonal forward-left / forward-right |
| Stick DOWN + X, DOWN + B | diagonal back-left / back-right |
| Stick LEFT + Y, RIGHT + Y | rotate left / rotate right |
| Let go of the stick | STOP |
| D-pad UP / DOWN | speed 25 / 50 / 75 / 100 % |
| Hold A | 100 % while held |
| LB + RB + START, the red **STOP ALL** button, or the SPACE key | STOP ALL (e-stop) |
| **Reset e-stop** button, then let go of the stick | drive again |

## Controls — Buttons style (14 buttons, both sticks ignored)

Choose it with **Control style → Buttons** in the Drive section. iPhone and iPad start on it.

| Do this | Motion |
|---|---|
| D-pad UP / DOWN / LEFT / RIGHT | forward / backward / strafe left / strafe right |
| D-pad UP + X, UP + B (or UP + LEFT, UP + RIGHT together) | diagonal forward-left / forward-right |
| D-pad DOWN + X, DOWN + B (or DOWN + LEFT, DOWN + RIGHT together) | diagonal back-left / back-right |
| D-pad LEFT + Y, RIGHT + Y | rotate left / rotate right |
| Let go of the D-pad | STOP |
| RT / LT | speed one level faster / slower |
| Hold A | 100 % while held |
| LB + RB + START, or the red **STOP ALL** button | STOP ALL (e-stop) |
| BACK, or the **Reset e-stop** button | reset the e-stop |

## Controls — Combined style (left stick or D-pad)

Choose it with **Control style → Combined**.

| Do this | Motion |
|---|---|
| Left stick **or** D-pad: UP / DOWN / LEFT / RIGHT | forward / backward / strafe left / strafe right |
| Stick pushed to a corner, or two D-pad directions together | the four diagonals |
| UP + X, UP + B, DOWN + X, DOWN + B | the four diagonals (as in the other styles) |
| LEFT + Y, RIGHT + Y | rotate left / rotate right |
| Let go | STOP |
| RT / LT | speed one level faster / slower |
| Hold A | 100 % while held |
| LB + RB + START, or the red **STOP ALL** button | STOP ALL (e-stop) |
| BACK, or the **Reset e-stop** button | reset the e-stop |

If the stick and the D-pad are used at the same time, the D-pad wins.

## Seeing the commands arrive

While driving is ON, the **CHAIN** line in the Drive section shows what the robot reports back:
commands sent by the page, commands accepted by the robot, the robot's state and speeds, the
one-way latency, and which bridge (tablet app) and ESP32 firmware answered.

## Files

| File | Purpose |
|---|---|
| `index.html` | the page (all the code, with comments) |
| `mqtt.min.js` | MQTT.js 5.16.0 browser build (MIT licence, see `MQTT-LICENSE.md`) |
| `manifest.json`, `icon-192.png`, `icon-512.png` | "Add to Home Screen" app icon |

**No password is stored in this repository.** The EMQX password is typed once on each
device (in **Settings**) and stays on that device.

## First time on a device

1. Open the link.
2. In **Robot link → Settings**, type the EMQX user name and password (port **8084**, path `/mqtt`).
3. Tap **Connect**. The robot shows `online` when the tablet app *final1* is running.
4. Plug in the controller and press any button.
5. Tap **Enable driving**. Motion commands are sent only while it says **Driving: ON**.

## Safety

- Driving switches itself **OFF** (and zeros are sent) when the page is hidden, loses focus,
  the link drops, or you disconnect. Tap **Enable driving** again to continue.
- No controller, or the Learn wizard open = zeros.
- Use only **one** operator at a time: this page **or** `robot_operator.py`.
- First test: Rob2 on a box, wheels off the ground.
