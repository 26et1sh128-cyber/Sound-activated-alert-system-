This project describes an Arduino-free clap-activated LED alert system. A KY-038 sound sensor detects a loud
clap and provides a digital trigger to an NE555 timer configured in monostable mode.
1.2 Problem Statement
The timer produces a pulse of approximately five seconds. A BC547 transistor is used as a switch to drive a red
LED. The system is powered by a 9V battery, with a regulated 5V supply used for the sound sensor.
Component Quantity
KY-038 sound sensor 1
NE555 timer 1
BC547 NPN transistor 1
Red LED 1
47 kΩ resistor 1
10 kΩ resistor 1
1 kΩ resistor 1
470 Ω resistor 1
100 µF electrolytic capacitor 1
10 nF capacitor 1
100 nF bypass capacitor 1 (recommended)
9V battery and clip 1
5V regulator (7805 or suitable converter) 1
Regulator input/output capacitors 0.33 µF input, 0.1 µF output
Breadboard and wires As needed
4.1 Block Diagram & Working Principle
Connect the 9V battery positive to the NE555 supply pins (pins 4 and 8) and the LED resistor branch. Feed the
KY-038 from a regulated 5V output. A 7805 linear regulator can be used if wired according to its datasheet, with
0.33 µF input and 0.1 µF output capacitors near the regulator. A suitable converter may also be used. Battery
negative and all circuit grounds must be common. Verify the regulator output is 5V before connecting the sensor.
4.2 Circuit Schematic & Pin Layout
Pin Connection
1 GND
2 KY-038 DO (active-low pulse; verify)
3 1 kΩ resistor to BC547 base
4 +9V (RESET)
5 10 nF capacitor to GND
6 Join to pin 7; timing capacitor node
7 Join to pin 6; timing resistor node
8 +9V
Timing network: join pins 6 and 7. Connect 47 kΩ from +9V to the joined pins 6/7 node. Connect the 100 µF
capacitor positive to the node and negative to GND. Add 100 nF between pins 8 and 1 close to the IC.
4.3 PCB Layout & Design
KY-038 VCC → regulated +5V; GND → common ground; DO → NE555 pin 2. AO is not used. Add a 10 kΩ
pull-up from pin 2 to the regulated 5V if required by the module output. Check the output logic before connecting;
the 555 trigger should be LOW briefly to acti
6.1 Experimental Setup
NE555 pin 3 → 1 kΩ → BC547 base. BC547 emitter → common ground. BC547 collector → LED cathode. LED
anode → 470 Ω resistor → +9V. Confirm the BC547 pinout for the specific part and the LED polarity before
powering.
1. Confirm the 5V regulator output using a multimeter before connecting KY-038.
2. Build the NE555 timing circuit with power disconnected.
3. Check sensor DO idle and trigger behavior; confirm a LOW trigger pulse is suitable.
4. Wire the BC547 and LED output stage; inspect polarity and transistor pinout.
5. Power the circuit and adjust the KY-038 trimmer until claps trigger reliably.
6. Test repeated claps and note that loud non-clap sounds may also trigger.
6.2 Measurements & Observations
For a 555 monostable, T ≈ 1.1 × R × C. With R = 47 kΩ and C = 100 µF: T ≈ 1.1 × 47,000 × 0.0001 ≈ 5.17
seconds.
6.3 Results & Performance Analysi
   7.1 Key Achievements
The circuit demonstrates an electronic alert using sound sensing, a 555 timer and transistor switching. A clap
triggers the sensor, the NE555 creates a timed output pulse, and the BC547 switches the LED. It operates without
Arduino or programming.
7.2 Limitations & Constraints
The KY-038 senses sound amplitude and cannot reliably distinguish a clap from other loud sounds. Component
pinouts can vary, so consult datasheets.
7.3 Future Scope
in future we would try to make this with arduino
Figure 7.1: side view
7.4 Conclusion
This is a low-voltage circuit. Disconnect the battery while wiring. Do not feed 9V directly into the KY-038 VCC.
Use a regulated sensor supply and common ground. The KY-038 senses sound amplitude and cannot reliably
distinguish a clap from other loud sounds. Component pinouts can vary, so consult datasheets.
