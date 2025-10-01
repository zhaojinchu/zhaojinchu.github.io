---
layout: page
title: Switcherooni Light Switcher
description: An automatic light switch flicker, controlled over bluetooth
img: assets/img/3.jpeg
importance: 3
category: fun
related_publications: false
profile_date: 2025-09-12
profile_importance: 3
profile_summary: A fun small servo powered light switch flicker, attached onto a light switch plate using the existing screws.
---

Switcherooni started as a “what if I could flick the dorm lights from bed?” idea and turned into a three-iteration Bluetooth-controlled servo rig. I modelled and printed the enclosures, tuned the electronics, and built the firmware that listens for BLE packets and translates them into smooth switch throws.

**Mk1 baseline**
- Took inspiration from James Hobson’s build but refactored the arm geometry to keep torque inline with the toggle.
- ESP32-S2 prototype driving an S51 micro servo directly from USB power—enough to prove the concept, but torque-starved.
- Fusion360 CAD printed on BambuLab X1 Carbon (PETG) with quick-release mounting so I could iterate overnight.

**Mk2 refinements**
- Upgraded to a HS-311 servo for more headroom, reworking the enclosure for rigidity and better clamp distribution.
- Learned the hard way that off-the-shelf servo CAD is rarely accurate—shimmed with washers to recover clearance and captured those tolerances in the next rev.
- Separated the bracket and electronics bay to isolate vibration and make servo swaps painless.

**Mk3 production build**
- Arduino Nano RP2040 Connect handles BLE, advertising on a three-second interval to stretch battery life (~4 days on three AA rechargeables).
- Hex commands (`0x01` / `0x00`) fire position presets; firmware maps them to servo pulse widths with debounce logic so the switch never chatters.
- Added a boost converter to give the servo a stable 6V rail while keeping the microcontroller happy at 3.3V.

**Control + future work**
- Currently controlled via a barebones mobile BLE terminal—UI next on the list alongside scheduling and multi-device support.
- Looking into swapping the Nano for an nRF52 and a proper Li-ion pack to push battery life into multi week territory.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/3.2.gif" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Switcherooni Mk3 demo showing the BLE controlled thro (albeit failing).
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.1.png" title="Switcherooni CAD" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Final CAD assembly with servo bay, clamp, and adjustable horn.
</div>

Next up: design a PCB to consolidate power management and BLE, then package the project for other lazy light switch aficionados.
