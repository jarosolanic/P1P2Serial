# Commands for Daikin F-series (VRV / Sky air) models

Some of the Daikin F-series models communicate systems parameters between the main controller and auxiliary controller in packet types 30-3F. Most intersting are packet type 38 (for FDY125LV1, FXMQ200PWM, and several others) or 3B (for FDYQ180MV1).

Some of these parameters can be changed, one at a time, by P1P2Monitor - when acting as an auxiliary controller (L1 mode) - using the P1P2Monitor command 'F'. In a future release these commands will be automatically generated by the ESP interacting with Home Assistant.

The F command format is
`F <packet-type> <payload-index> <new-value>`
with packet-type and new-value hexadecimal, and payload-index in decimal format. If you hate spaces, you may concatenate these using a 2-char packet-type and 2-byte parameter number: `F38 0 1` is equivelant to `F380001`.

Some example parameters and commands (these may or may not work on other models):

## FDYL125LV1, FXMQ200PWM, some other models

As an example, payload byte 0 in packet type 38 is used for switching cooling/heating off.

| Command  | Description                                        |
|:---------|:-----------------------------------------------
| `F 38 0 1`   | to switch on
| `F380001`    | to switch on (alternative without spaces)
| `F 38 0 0`   | to switch off
| `F 38 1 61`  | to set heating mode
| `F 38 1 62`  | to set cooling mode
| `F 38 1 63`  | to set auto mode
| `F 38 1 67`  | to set dry mode
| `F 38 1 60`  | to set fan-only mode
| `F 38 2 17`  | to set the setpoint to 0x17 = 23C (cooling mode)
| `F 38 2 19`  | to set the setpoint to 0x19 = 25C
| `F 38 4 11`  | to set the fanmode to low         (cooling mode)
| `F 38 4 31`  | to set the fanmode to medium
| `F 38 4 51`  | to set the fanmode to high
| `F 38 6 17`  | to set the setpoint to 0x17 = 23C (heating mode)
| `F 38 6 19`  | to set the setpoint to 0x19 = 25C
| `F 38 8 11`  | to set the fanmode to low         (heating mode)
| `F 38 8 31`  | to set the fanmode to medium
| `F 38 8 51`  | to set the fanmode to high

## FDYQ180MV1, possibly others

As an example, payload byte 0 in packet type 3B is used for switching cooling/heating off.

| Command  | Description                                        |
|:---------|:-----------------------------------------------
| `F 3B 0 1`   | to switch on
| `F3B0001`    | to switch on (alternative without spaces)
| `F 3B 0 0`   | to switch off
| `F 3B 1 61`  | to set heating mode
| `F 3B 1 62`  | to set cooling mode
| `F 3B 1 63`  | to set auto mode
| `F 3B 1 67`  | to set dry mode
| `F 3B 1 60`  | to set fan-only mode
| `F 3B 2 17`  | to set the setpoint to 0x17 = 23C (cooling mode)
| `F 3B 2 19`  | to set the setpoint to 0x19 = 25C
| `F 3B 4 11`  | to set the fanmode to low         (cooling mode)
| `F 3B 4 31`  | to set the fanmode to medium
| `F 3B 4 51`  | to set the fanmode to hig
| `F 3B 6 17`  | to set the setpoint to 0x17 = 23C (heating mode)
| `F 3B 6 19`  | to set the setpoint to 0x19 = 25C
| `F 3B 8 11`  | to set the fanmode to low         (heating mode)
| `F 3B 8 31`  | to set the fanmode to medium
| `F 3B 8 51``  | to set the fanmode to high
| `F 3B 16 ??` | (not sure yet, active hvac zones related)
| `F 3B 17 ??` | (not sure yet, target fan mode related)