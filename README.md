# PicoMotion - simple motion sensor for Home Assistant
PicoMotion is an open-source, simple, ready-to-mount, and ready-to-use motion sensor designed to be easily mounted on a wall, even upside down, to be easily adjusted for the use case and to flawlessly work within Home Assistant, by the means of ESPHome.

## Hardware
The hardware is comprised of:
- WeMos D1 Mini ESP8255 Development Board
- HC-SR501 PIR Sensor
- 3D printed enclosure (STLs provided)

## Software
The firmware is written with ESPHome tool, flashed either via ESPHome-flasher, or from ESPHome Add-on within Home Assistant the first time. Afterward it can be OTA flashed. (both .yaml and compiled .bin provided)

## Open-source
As the sensor is made using open-source hardware and software, the whole kit is also open-source, so feel free to come up with feedback, use it, improve it and share it.

Thanks to Home Assistant and ESPHome! The core of the sensor is based on these two amazing pieces of software.

#### Adding to the below instructions, I highly recommend reading the Quick Start guide, provided in this repo.

# Instructions
1. After you got all the needed parts, you need to flash the firmware on the D1 mini.

Method 1: Download and use the .bin file in this repo, connect your D1 mini/ESP-based MCU to your PC using a micro-USB cable and flash the file on the board using ESPHome-flasher utility, for your OS. (https://github.com/esphome/esphome-flasher/releases)

Method 2: If you already have ESPHome Add-on installed, then create a new node, use and modify accordingly the .yaml file provided in this repo and flash your D1 mini directly from the system running ESPHome.

2. Disconnect power and connect the PIR Sensor to GND, 5V and Signal pin (default: D4 on D1 mini, for visual blue led feedback on motion detection).

3. Use the recommended 5V/1Amp DC power supply for powering the D1.

4. If you have added a new node in ESPHome Add-on and changed the WiFI SSID already, then your device should appear online after a few seconds and be recognized by auto-discovery feature of your Home Assistant.
If you did flashed the .bin file in this repo, then wait a few minutes, as the D1 will fail to connect to the SSID a few times and will eventually enable a hotspot AP, named Picomotion X (where X should be a unique number across your PicoMotion devices on the local network). Connect to the hotspot, dismiss the alerts of having "No Internet", navigate to http://192.168.4.1 using a browser, select your preffered WiFi network, type the password and hit "Save". The D1 will reboot and connect to your WiFi network.

5. After Home Assistant dicovery notfies you (if not, you can trigger that by manually restarting the Server), you can configure the new ESPHome node using the Integrations wizard and providing the api password, which is set in the .yaml file. You will get by default a motion class binary sensor, which gets triggered by warm bodies, like humans/animals. 
#### Note: If using the provided .bin file, the random api password for the provided sample is: HDLlLT2YEIci

6. Enjoy using the motion sensor in your light automations, presence detection ideas, alarm system or whatever. You can adjust the sensitivity and delay after trigger, using the two knobs, on top of the sensor.

# 3D enclosure instructions
1. Slice the STLs in your preffered slicer. The settings in CURA 4.8.0, for a Creality Ender-5, used for printing the sample in the pictures are:
- 0.2 layer height
- 20% infill
- 1.2 wall thickness
- 200C print temperature (differs for each material; for the sample Premium PLA/PHA was used)
- 40mm/s print speed
- Touching Buildplate support (for the sensor bottom especially)

2. Insert the D1 mini in the case, letting the headers facing upwards and use a small amount of superglue, to fix it on the back of the support.

3. Mount the support on the wall, using the appropiate screw for your material.

4. Push the PIR sensor in the case, connect 3 jumper wires to the pins on the back, assemble the back of the sensor.

5. Insert the printed tightening ring onto the shaft of the sensor, insert the sensor on the spherical mount, adjust it's position and secure it by pulling down the ring.

6. Connect the jumper wires to the D1 on the left-side header, from top to bottom (5V, GND, D4).

Credits:
- Home Assistant (https://www.home-assistant.io/)
- ESPHome (https://esphome.io/)
- Thingiverse (https://www.thingiverse.com/)
    
    especially:

        - BrainFever (https://www.thingiverse.com/brainfever/designs)
        
        - Electronlibre (https://www.thingiverse.com/electronlibre/designs)
        
        - Hills8 (https://www.thingiverse.com/hills8/designs)