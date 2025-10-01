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

Switcherooni Mk1:

Inspired design from James Hobson: https://hackaday.com/2017/12/10/light-switch-for-the-lazy/.

Used a S51 servo – wasn’t powerful enough and had trouble flicking most light switches
CAD using Fusion360, and printed on roboclubs BambuLabs X1 Carbons using PETG filament
Initially tested using an ESP32 S2, which didn’t have BLE. Later projects will upgrade to BLE solution
Used direct 5V from ESP32 board (not recommended) and powered using a micro-usb cable connected to my phone / laptop


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/3.2.gif" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Switcherooni Mk1 demo video.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.1.png" title="Switcherooni CAD" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    CAD Model
</div>


Switcherooni Mk2:

Upgraded design to use a HS-311 servo. Redesigned CAD model to fit the new servo and partially redesigned the base plate to be more structurally stable. Printed using same settings.
Misaligned CAD from using inaccurate CAD modellings of the servo and servo horn. This means that the servo was too close to the base plate. Shimmied together some thick rubber washers and some steel washers to lift the entire servo up by roughly 12 mm. However, although the horn attachment could now move above the base plate, it was too close to the base plate. This mean that the moments were not optimal to flick the light switch. Optimally, you would want the top part flicked only. 


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.1.png" title="Switcherooni CAD" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    CAD Model
</div>

Switcherooni Mk3:

Redesigned CAD again, added 17mm to the servo attachment arms. The final working version, connected via BLE to a Arduino Nano RP2040 Connect through a mobile bluetooth connection. Hex values are sent of 0x01 or 0x00 corresponding to ON or OFF. The bluetooth signals are interpreted on the microcontroller which then sends the corresponding pulse time to the servo. Powered currently using 3 AA rechargable batteries (~3.6V) for the microcontroller, stepped up to 6V for the servos. Bluetooth is designed to advertise only every 3 seconds, with lower BLE TX power. Estimated battery life of ~4 days.

Future Notes:

- A mobile app with a proper interface would be nice, currently have to connect to peripheral and send out hex codes manually. 
- Maybe an Arduino Nano wasn't the smartest choice for battery life. 
- Lets try with something like a nRF52 and a larger Li-ion next time, maybe it might actually be feasible in my dorm room!
