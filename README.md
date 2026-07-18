# Gyro Games (snakegame_pilot)

A single-file HTML page with two small canvas games behind a tab bar: a classic Snake game and a "Gyro Ball" physics toy. Built as a GitHub Copilot experiment (hence the `_pilot` in the repo name).

Live: https://vaibhavkumar.is-a.dev/snakegame_pilot/

## The games

**Snake** — classic grid snake on a 400x400 canvas (20px cells). Eat the food, grow, don't hit the walls or yourself. Score and session-best are tracked.

Controls:
- Keyboard: arrow keys or WASD (any key starts/restarts)
- Touch: swipe on the canvas, or use the on-screen D-pad (shown on touch devices)
- Tilt: on mobile, "Enable Tilt Controls" steers the snake with the device gyroscope (tilt past 15° to turn)

**Gyro Ball** — tilt your phone/tablet to roll a ball around the screen. Real-ish physics: tilt maps to acceleration, with friction and bouncy wall collisions. Three render styles to cycle through (shiny chrome, rocky stone, glass marble), each drawn with canvas gradients and rotating texture.

## How it works

- Everything is in one `index.html`: styles, markup, and ~500 lines of vanilla JS. No dependencies, no build step.
- Snake runs on a `setInterval` game loop; Gyro Ball on `requestAnimationFrame` with delta-time physics.
- Tilt input uses the `deviceorientation` event, with iOS permission prompting (`DeviceOrientationEvent.requestPermission`) and orientation-angle correction so landscape iPads tilt the right way.

## Run locally

```sh
open index.html
```

Gyro features need a device with orientation sensors (and HTTPS or localhost for the iOS permission prompt); keyboard/touch Snake works anywhere.
