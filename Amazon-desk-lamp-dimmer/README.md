# LED-Desk-Lamp-Dimmer
Nano powered Desk Lamp Dimmer Controller. 
Made as a replacement for a cheap amazon USB Desk Lamp.  The controller it came with burnt out but the lights were still good. We've got a couple of these around the house so I suspect they will all got the same way.

It is controlled by a rotary encoder with a switch. If you press the switch you can cycle between the white lights being on, the amber lights being on or both being on. If you long press the switch it turns the lights off. When in the off mode the light uses 0.015A. The light remembers the previous brightness setting as you cycle between modes and off state, but not after being unplugged.

The Arduino controls two IRLZ44N mosfets which control the lights. The coding was fun ( I needed to get chatgpt to help with some of the logic as I couldn't work out the if statements. I also needed to restrict the pwm to stop the light being too bright and to try to match the colour levels when both light are on for a warmer tone.

There was a fair bit of troubleshooting with the wiring. Initially I used the wrong mosfets (IRFZ44N) which whilst it looked to be working gave some weird frequencies when I tested the drain and wasn't being fully cycled by the 5V of the Arduino.

I also found that when powered of the same 5V supply as the lights the Arduino kept shutting down. I got round this by adding a couple of 100uF decoupling capacitors, one near the mosfets and one near the arduino. The solved that problem.

Finally when it came time to actually swap the mosfets for the logic level equivalents nothing worked properly. I initially thought that it was the fets but after plugging in the arduino via usb to my pc to get serial output for troubleshooting, everything worked, suggesting that the issue was the arduino. After swapping the 5v supply from vin to 5V pin everything worked.

And that's basically that.

I think that it works, but if anyone has any feedback please let me know. I've attached an attempt at a sketch below. I couldn't find a component that had a rotary encoder with the switch built in so have modelled them as two separate things.

I think I've learned a fair bit from doing this. Things not working kind of forces you to try and understand and along the way you pick up more (I orginally didn't have the resistors is series to the gate for example). Thanks to everyone in the form who helped me do this.

Next step will be to solder it up on some perf board and do a 3D printed enclosure.

EDIT: I almost forgot another issue I hit. The LED's buzzed! That was a surprise. But it taught me that I could change the pwm frequency of the arduino which was super helpful. Oh and getting the rotary encoder to stay in the breadboard. Thank you kind youtuber for mentioning that rotating the pins 90 degrees makes them stay in!

