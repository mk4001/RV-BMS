# RV-BMS

RV-BMS is an iPhone, iPad, Apple CarPlay and Apple Watch app that reads the Bluetooth battery management system (BMS) of lithium batteries used in RVs, campers, vans and boats.

The app connects to the BMS over Bluetooth Low Energy, decodes its data locally on the iPhone and shows charge, power, every cell, temperatures and alarms. The same data drives a Lock Screen Live Activity, widgets, a CarPlay interface with spoken status, an Apple Watch app with complications, and a 30-day history.

> RV-BMS is an independent application. It is not affiliated with, endorsed by, or sponsored by PowerQueen, Redodo, LiTime, Starry Sea, JK (Jikong), JBD (Xiaoxiang), Daly or any other battery or BMS manufacturer. All trademarks belong to their respective owners.

- Marketing site: <https://www.mf-lab.com/RV-BMS_MKTG.html>
- Privacy policy: <https://www.mf-lab.com/RV-BMS_Privacy-Policy.html>
- Support: <https://www.mf-lab.com/support/>

## Contents

- [Features](#features)
- [Free and Pro](#free-and-pro)
- [Supported batteries](#supported-batteries)
- [Requirements](#requirements)
- [Getting started](#getting-started)
- [Understanding the values](#understanding-the-values)
- [History and CSV export](#history-and-csv-export)
- [Live Activity and widgets](#live-activity-and-widgets)
- [CarPlay](#carplay)
- [Apple Watch](#apple-watch)
- [Background operation](#background-operation)
- [Troubleshooting](#troubleshooting)
- [Reporting a problem](#reporting-a-problem)
- [How it works](#how-it-works)
- [Privacy](#privacy)
- [Known limitations](#known-limitations)
- [Credits](#credits)

## Features

- Direct Bluetooth LE connection to the battery's BMS, no gateway or extra hardware.
- Dashboard: state of charge, voltage, current, power, remaining capacity, time to empty or to full.
- Every cell voltage, with the lowest and highest cell, the cell difference and balancing cells.
- State of health, cycles, full capacity, temperatures, charge and discharge status, BMS alarms.
- Readings every 2 seconds in the foreground and every 5 seconds in the background.
- Automatic reconnection when the battery is back in range.
- 30-day history with charts, charged and discharged energy, CSV export.
- Live Activity on the Lock Screen and in the Dynamic Island.
- Home Screen widgets (small, medium), Lock Screen widgets (circular, rectangular, inline), CarPlay widgets.
- Apple CarPlay interface with spoken status in English, Italian, French, German or Spanish.
- Apple Watch app and watch face complications (circular, rectangular, inline, corner).
- Demo mode with a simulated battery, to try every feature without hardware.
- No account, no server, no analytics.

## Free and Pro

| | Free | RV-BMS Pro |
| --- | --- | --- |
| iPhone and iPad app with your battery: dashboard, cells, details | Yes | Yes |
| History, charts, energy, CSV export | Yes | Yes |
| Demo mode on every screen | Yes | Yes |
| CarPlay with your battery, voice readouts | Demo mode only | Yes |
| Apple Watch app and complications with your battery | Demo mode only | Yes |
| Live Activity with your battery | Demo mode only | Yes |
| Home Screen, Lock Screen and CarPlay widgets with your battery | Demo mode only | Yes |

RV-BMS Pro is a one-time purchase (no subscription). Without Pro, CarPlay, the Apple Watch, the Live Activity and the widgets show a lock and "RV-BMS Pro" when a real battery is selected; with the demo battery they always work.

Purchase, restore and refund: **⚙︎ menu › RV-BMS Pro**. The **Manage Purchase** section shows the purchase status and date, **Restore Purchases**, and **Request a Refund** (Apple's refund sheet; refunds are decided by Apple).

## Supported batteries

Your battery must have a **Bluetooth BMS**. RV-BMS recognises it automatically from its Bluetooth advertisement.

| BMS family | Found in | Status | Values |
| --- | --- | --- | --- |
| Redodo BMS | PowerQueen, Redodo, LiTime, Starry Sea | **Tested** on a real battery (PowerQueen 12.8 V 100 Ah) | Charge, voltage, current, power, remaining and full capacity, health, cycles, every cell, temperatures, balancing, alarms |
| JK (Jikong) | DIY and RV LiFePO4 packs | **Beta** | Charge, voltage, current, capacity, health, cycles, every cell, up to six temperatures, charge and discharge status, balancer, alarms |
| JBD (Xiaoxiang) | Many drop-in LiFePO4 batteries | **Beta** | Charge, voltage, current, capacity, cycles, every cell, temperatures, balancing, charge and discharge status, alarms |
| Daly | Daly Bluetooth BMS modules | **Beta** | Charge, voltage, current, remaining capacity, cycles, every cell, temperatures, charge and discharge status, alarms |

**Tested** means verified with RV-BMS on a real battery. **Beta** protocols are verified against data recorded from real batteries (see [How it works](#how-it-works)) and are waiting for field confirmation. If you have a beta battery, a report that it works (or doesn't) is very welcome: see [Reporting a problem](#reporting-a-problem).

How each family is recognised:

| BMS family | Bluetooth name | Other conditions |
| --- | --- | --- |
| Redodo | `P-12…`, `P-24…`, `PQ-12…`, `PQ-24…`, `R-12…`, `R-24…`, `RO-…`, `L-12…`, `L-24…`, `L-51…`, `LT-…` (recent serials), `S-…`, `SS-…` | Service `FFE0` and manufacturer ID `0x585A` |
| JK | any | Service `FFE0` and manufacturer ID `0x0B65` or `0x4B4A` |
| JBD | `JBD-…`, `LSG-…`, `N-?????BL…`, `SJ-???-…`, `SX1…`, `SX60…`, `SBL-…`, `OGR-…`, `TZ-H…`, `12???BL…`, `24???BL…` | Service `FF00` |
| Daly | `DL-…` | Service `FFF0`, or a Daly manufacturer ID |

Not supported:

- Victron devices: use VE-Display.
- Batteries without a Bluetooth BMS, or with Wi-Fi/cloud-only monitoring.
- JBD batteries protected by a Bluetooth password.

## Requirements

- iPhone or iPad with iOS / iPadOS 17 or later.
- Bluetooth permission for RV-BMS (asked at first launch).
- A compatible battery with a Bluetooth BMS, within Bluetooth range (typically a few metres).
- Optional: Apple Watch with watchOS 10 or later, paired with the iPhone.
- Optional: a car with Apple CarPlay.

## Getting started

1. **Close the battery manufacturer's app** on every phone or tablet nearby. Most BMS accept only one Bluetooth connection at a time.
2. Open RV-BMS near the battery and allow Bluetooth when asked.
3. Compatible batteries appear under **Nearby batteries**, with their protocol and signal strength.
4. Tap your battery. RV-BMS connects and shows the dashboard. Next time it reconnects on its own.

No battery at hand? Tap **Try demo mode** on the first screen. The demo battery cycles through discharge, rest and charge, and comes with 24 hours of sample history.

To change battery: **⚙︎ menu › Batteries**. To remove it: **Forget this battery**.

## Understanding the values

| Value | Meaning |
| --- | --- |
| Charge (SOC) | State of charge reported by the BMS, in %. |
| Voltage | Pack voltage. On Redodo/PowerQueen batteries this is the sum of the cell voltages; the BMS's own pack measurement is in Details as *BMS measured voltage* (it can be about 0.1–0.2 V lower). |
| Current | Positive while charging, negative while discharging. |
| Power | Voltage × current. Green while charging, orange while discharging. |
| Remaining | Remaining capacity counted by the BMS, in Ah. |
| Time to empty / Time to full | Remaining (or missing) Ah divided by the current. Shown only when the current is at least 0.1 A; at rest it shows *Idle*. |
| Cells | Every cell voltage. The lowest cell is orange, the highest blue; **Δ** is the difference between them. ⇄ marks cells being balanced. |
| Health (SOH) | State of health reported by the BMS. Some BMS report more than 100% when the measured capacity exceeds the nominal one. |
| Charging / Discharging | *Cut off by BMS* means the BMS has opened that path (protection). |
| Status | *OK*, or the BMS protection and fault codes in hexadecimal. |

## History and CSV export

**⚙︎ menu › History**

- RV-BMS saves one point per minute (average voltage, current and power; last state of charge; lowest and highest cell; highest temperature), also in the background, for each battery separately.
- Ranges: 1 h, 6 h, 24 h, 7 days, 30 days. Long ranges are averaged (5 min, 30 min, 2 h) to keep the charts smooth.
- Metrics: charge, power, current, voltage, temperature, cell difference. Touch and hold a chart to read a value.
- Gaps (app closed, battery out of range) are not joined by a line.
- **Charged / Discharged** energy is the integral of the per-minute power; gaps longer than 5 minutes are not counted.
- History older than 30 days is deleted automatically. **Delete history for this battery** removes it at once.

**Export CSV** shares a file with these columns:

```text
timestamp,voltage_v,current_a,power_w,soc_pct,remaining_ah,min_cell_v,max_cell_v,max_temp_c,samples
```

`timestamp` is ISO 8601 (UTC), one row per minute; `samples` is the number of readings averaged in that minute.

## Live Activity and widgets

- **Live Activity**: ⚙︎ menu › **Live Activity**. It shows charge, power, voltage, current and time left on the Lock Screen and in the Dynamic Island, updated by the app in the background. It refreshes at most every 10 seconds (immediately when the charge %, the charging state or an alarm changes). After a minute without data it shows *Not updating*.
- **Widgets**: add them from the widget gallery (Home Screen, Lock Screen, CarPlay). iOS limits how often widgets can refresh, so RV-BMS updates them only when something meaningful changes (charge %, connection, charging) and at most every 5 minutes. For live values, use the Live Activity.
- If Live Activities are disabled, enable them in **Settings › RV-BMS › Live Activities**.

## CarPlay

1. Connect the iPhone to CarPlay and open RV-BMS from the CarPlay launcher.
2. The first row shows the battery, charge, power and connection.
3. Open **Overview** (charge, power, voltage, current, time left, remaining), **Cells** (difference, lowest, highest, each cell) or **Health** (alarms, health, cycles, temperatures, charge and discharge status).
4. Opening a page reads its values aloud through the car's audio; open it again to repeat.

Voice language: **⚙︎ menu › CarPlay voice** (English, Italiano, Français, Deutsch, Español, or Off). The values on screen refresh about once per second.

CarPlay works even when the iPhone app is not open on the phone: iOS starts it when the car connects.

## Apple Watch

- The Watch app installs together with the iPhone app (if automatic app install is on, or from the Watch app on iPhone).
- The iPhone sends the readings to the Watch: about every 2 seconds while the Watch app is open; for complications, when the charge or the connection changes, or once a minute.
- Main page: charge ring, power, voltage, current, time left. Swipe up for remaining Ah, temperature, cell difference, alarms and status.
- Complications: circular, rectangular, inline, corner. watchOS limits how often complications refresh, so they can lag behind the app by a few minutes.
- The iPhone must be nearby and RV-BMS connected to the battery on the iPhone.

## Background operation

RV-BMS uses the iOS `bluetooth-central` background mode:

- While the battery is connected, iOS wakes the app for each reading, so the Live Activity, widgets, Apple Watch and history stay up to date with the screen off.
- If iOS closes the app to free memory, it relaunches it in the background at the next Bluetooth event, for example when the battery comes back in range.
- **If you force-quit RV-BMS from the app switcher, iOS stops all background activity** until you open the app again. This is an iOS rule, not a setting of the app.
- Keeping a Bluetooth connection open uses a little battery on the iPhone.

## Troubleshooting

**The battery does not appear under Nearby batteries**

- Close the manufacturer's app on every device (phones, tablets, a second iPhone): the BMS accepts one connection.
- Get closer to the battery; metal battery compartments reduce the range a lot.
- Check **Settings › Privacy & Security › Bluetooth › RV-BMS** is on.
- Make sure the battery has a Bluetooth BMS and that its family is in [Supported batteries](#supported-batteries).
- JBD batteries are recognised by their Bluetooth name. If yours has a different name, it is not recognised yet: please report it with its exact name.

**It connects, but no values appear, or it keeps reconnecting**

- Another app or device is probably connected to the BMS. Close it and wait a few seconds.
- Move closer: at the edge of the range the connection drops and comes back.
- Turn Bluetooth off and on again, then reopen RV-BMS.

**Current shows 0 A with a small load**

The BMS measures current in steps (about 0.25 A on Redodo/PowerQueen batteries). Smaller loads read as 0 A; the remaining Ah still decreases.

**The voltage is different from my multimeter or charger**

See *Voltage* in [Understanding the values](#understanding-the-values). The app shows the sum of the cells; the BMS's own measurement is in Details. Voltage also changes under load and recovers slowly after the load is removed.

**The Live Activity says "Not updating"**

The app stopped receiving data: the battery is out of range, another app took the connection, or RV-BMS was force-quit. Open the app to reconnect.

**Widgets or complications are a few minutes behind**

That is expected: iOS and watchOS limit how often they refresh. Use the Live Activity or the Watch app for live values.

**The Apple Watch shows "Waiting for iPhone" or "No battery selected"**

Open RV-BMS on the iPhone, make sure a battery (or demo mode) is selected and connected, and keep the iPhone near the Watch.

**CarPlay, the Watch, the widgets or the Live Activity show a lock and "RV-BMS Pro"**

A real battery is selected and RV-BMS Pro is not active. Buy or restore it in **⚙︎ menu › RV-BMS Pro**, or select demo mode to try those features.

**I bought Pro but it is not active**

**⚙︎ menu › RV-BMS Pro › Restore Purchases**, signed in with the same Apple Account used for the purchase.

**Health shows more than 100%**

Some BMS report a measured capacity higher than nominal (for example 105 Ah on a 100 Ah battery). The value comes from the BMS.

## Reporting a problem

Open an issue on this repository, or use the [support page](https://www.mf-lab.com/support/). Please include:

- iPhone (and Apple Watch) model, iOS (and watchOS) version, RV-BMS version (⚙︎ menu › About).
- Battery brand and model, and its **exact Bluetooth name** as shown in RV-BMS or in the manufacturer's app.
- What you expected and what happened, with screenshots.
- For wrong values: the value shown by RV-BMS and by the manufacturer's app at the same moment.
- If useful, a CSV export of the history (⚙︎ menu › History › Export CSV).

For beta batteries (JK, JBD, Daly), a short "it works" report with the battery model is just as useful.

## How it works

RV-BMS connects to the BMS as a Bluetooth LE central (GATT client), subscribes to its notify characteristic and sends the status requests of its protocol. **It only sends read requests: it never sends commands that change the BMS settings.**

| BMS family | Service | Notify / Write | Requests per refresh |
| --- | --- | --- | --- |
| Redodo | `FFE0` | `FFE1` / `FFE2` | `00 00 04 01 13 55 AA 17` → one 105-byte status frame |
| JK | `FFE0` | `FFE1` / `FFE1` | device info `0x97` once (firmware → frame layout), then cell info `0x96`; the BMS then streams about once per second |
| JBD | `FF00` | `FF01` / `FF02` | `DD A5 03 00 FF FD 77` (basic info), then `DD A5 04 00 FF FC 77` (cell voltages) |
| Daly | `FFF0` | `FFF1` / `FFF2` | Modbus-style register reads; variant `D2` or `0x81` detected automatically |

Redodo status frame (little-endian), as decoded by RV-BMS:

| Offset | Size | Field |
| --- | --- | --- |
| `0…2` | 3 | Header `00 00 <length>` |
| `8` | 4 | Pack voltage measured by the BMS, mV |
| `12` | 4 | Sum of cell voltages, mV |
| `16` | 16 × 2 | Cell voltages, mV (0 = no cell) |
| `48` | 4 | Current, mA (signed) |
| `52`, `54`, `56` | 2 each | Temperatures: cells, MOSFET, auxiliary, °C |
| `62` | 2 | Remaining capacity, Ah × 100 |
| `64` | 2 | Full capacity, Ah × 100 |
| `68` | 4 | Heater |
| `76`, `80` | 4 each | Protection state, fault state |
| `84` | 4 | Balancing cells bitmask |
| `88` | 2 | Battery state |
| `90` | 2 | State of charge, % |
| `92` | 4 | State of health, % |
| `96` | 4 | Cycles |
| `100` | 4 | Total discharged, Ah |
| last | 1 | Checksum: sum of all previous bytes, modulo 256 |

Verification: the Redodo decoder is tested against frames read from a real PowerQueen battery. The JK, JBD and Daly decoders are tested against the frames recorded from real batteries in the test suite of the open-source [aiobmsble](https://github.com/patman15/aiobmsble) project, compared field by field with aiobmsble's own decoding (JK firmware 10.x to 19.x, Daly D2 and 0x81 variants, JBD).

## Privacy

- No personal data collection, no analytics, no tracking.
- No account, no server: battery data is decoded and stored only on the device.
- Data reaches the Apple Watch directly from the iPhone (WatchConnectivity) and CarPlay through the iPhone.
- Purchases are handled entirely by Apple.

Full policy: <https://www.mf-lab.com/RV-BMS_Privacy-Policy.html>

## Known limitations

- JK, JBD and Daly support is in beta: verified against recorded data, not yet confirmed with RV-BMS on real batteries.
- JBD batteries are recognised only by the Bluetooth names listed above (iOS does not expose the Bluetooth MAC address, which other tools use to recognise them). Password-protected JBD BMS are not supported.
- One battery at a time.
- Background updates stop if the app is force-quit from the app switcher (iOS rule).
- Widgets and complications refresh less often than the app, because of iOS and watchOS limits.
- Current resolution depends on the BMS (about 0.25 A on Redodo/PowerQueen).

## Credits

The JK, JBD, Daly and Redodo protocol decoders are ported to Swift from **[aiobmsble](https://github.com/patman15/aiobmsble)** by patman15, licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), and checked against its recorded test data.

PowerQueen, Redodo, LiTime, Starry Sea, JK, Jikong, JBD, Xiaoxiang and Daly are trademarks of their respective owners. RV-BMS is not affiliated with or endorsed by them.

© 2026 MF-Lab.com
