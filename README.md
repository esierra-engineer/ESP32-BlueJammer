<h1 align="center">ESP32-BlueJammer - by @emensta</h1>
<div align="center">
  <img src="https://dwdwpld.pages.dev/ESP32-BlueJammerBy@emensta.jpg" alt="ESP32-BlueJammer">
  <h3 align="center">Jamming is ILLEGAL! Educational purposes only!</h3>
</div>


## ESP32-BlueJammer
The ESP32-BlueJammer (Bluetooth jammer, BLE jammer, WiFi jammer, RC jammer) disrupts various devices using an ESP32 and nRF24 modules, causing plenty of noise and sending unnecessary packets (DoS).              
                                                                    
It interrupts:  
**The whole 2.4GHz broadband!** Everything that works on 2.4GHz is being interfered, like:                                                       
audio in speakers being transmitted over bluetooth, microphones on 2.4GHz, smartphone connections, WiFi, RC Drones (etc.), IoT devices, smart gadgets, wireless keyboard & mouse, just anything on 2.4GHz!

Ideal for controlled disruption and security testing. Based on 2.4GHz communication.

It has a big range (over 30Meters+ - may vary on your antenna and hardware setup!) on newest Bluetooth versions with casual 2.4GHz antennas, you can easily increase this as well by taking some simple "bigger" router antennas.
An amplifier (2.4GHz) may be a good option too!

Remember that jamming is illegal and should not be used with malicious intent!

---

## Operation Channels
- **Bluetooth** = 79CH  
  Frequency Range: 2.402 GHz to 2.480 GHz  
  Channel Width: 1 MHz

- **BLE** = 40CH  
  Frequency Range: 2.400 GHz to 2.4835 GHz  
  Channel Width: 2 MHz

- **WiFi** = 14CH  
  Frequency Range: 2.400 GHz to 2.4835 GHz  
  Channel Width: Typically 20 MHz, but can be 22 MHz or 40 MHz in some cases

- **RC drones, etc.** = 1-125CH  
  Frequency Range: 2.400 GHz to 2.525 GHz  
  Channel Width: 1 MHz



## How to use?
To disrupt various channels on the 2.4GHz band, do the following to enable your ESP32-BlueJammer:
- Every mode starts right away after powering on the device! There is no additional button to start the attack!  
- It simply jams right away once powered!

### Combo-Channel-Select_BT-BLE-WiFi-RC firmware:
- use the "Boot" button on the ESP32 to switch between the channel modes on the Combo-Firmware!
- the OLED will display your current operation channel
- the status LED lets you know about the current state you're in:  
1 blink = BT  
2 blinks = BLE  
3 blinks = WiFi  
4 blinks = RC  
- the serial output of your ESP32-BlueJammer will output the following lines when switching mode:  
State 1: Bluetooth  
State 2: Bluetooth Low Energy  
State 3: WiFi  
State 4: RC  

### all other firmware:
- the firmware you choose indicates the operation channel by its name, this means:

Bluetooth_80_CH - jams classic Bluetooth  
Frequency Range: 2.402 GHz to 2.480 GHz  

BluetoothLowEnergy_40_CH - jams Bluetooth Low Energy  
Frequency Range: 2.400 GHz to 2.4835 GHz  

Bluetooth-BluetoothLowEnergy_40-80_CH - jams classic Bluetooth & Bluetooth Low Energy  
Frequency Range: 2.402 GHz to 2.480 GHz & 2.400 GHz to 2.4835 GHz  

Bluetooth-WiFi_14-80_CH - jams classic Bluetooth & WiFi  
Frequency Range: 2.402 GHz to 2.480 GHz & 2.400 GHz to 2.4835 GHz  

WiFi_14_CH - jams WiFi  
Frequency Range: 2.400 GHz to 2.4835 GHz  

2.4GHzRemoteControl(Drones etc.)_1-125_CH - jams RC (Drones etc.)  
  Frequency Range: 2.400 GHz to 2.525 GHz  


## Hardware - Make your own ESP32-BlueJammer
(Aliexpress affiliate links to support me-linked to the item names)
### Required:

- **[ESP32 Dev Module](https://s.click.aliexpress.com/e/_onYIVKr)** (**Recommended: ESP32-32U CP2102**, any ESP32 should work as long as it has the needed pins)
- **[nRF24L01+PA+LNA](https://s.click.aliexpress.com/e/_oma5UQx)** (2x)
- **[10-100uF Capacitor](https://s.click.aliexpress.com/e/_oFvFeYX)** (2x) (any voltage above 5V)
- **[Prototype PCB](https://s.click.aliexpress.com/e/_oBtd18j)** (at least 7x9 cm, but you will need to cut it down to fit the 3D-printed case, which fits a size of 7x5,5cm!)

### Additional:

- **[0.96" OLED Display I2C](https://s.click.aliexpress.com/e/_oCdkjPX)**
- [3rd Antenna: **IPEX to SMA-F pigtail**](https://s.click.aliexpress.com/e/_oFDpn1V)
- [Status LED: **3mm LED**](https://s.click.aliexpress.com/e/_ooxufHV)
- **[4.7k Ohm Resistor](https://s.click.aliexpress.com/e/_oBV1Q1Z)**

### If you're looking to add a battery:

- **[3.7V Li-Ion Battery](https://s.click.aliexpress.com/e/_on04mQ7)**
- **[JST PH 2.0 Connector](https://s.click.aliexpress.com/e/_ooSOhDd)**
- **[TP4056 Charging Module (Micro-USB/Type-C)](https://s.click.aliexpress.com/e/_oCqORHE)**
- **[Mini Slide Switch](https://s.click.aliexpress.com/e/_ooC8DXh)**

### To screw the 3D printed case together you must have:

- **M3x16 Screws** (2x)  
- **M3 Nuts** (2x)  
Get this M3 kit instead:
- **[M3 screws&nuts kit](https://s.click.aliexpress.com/e/_oC24YXH)**



## Antennas
A frequently asked question is whether the antennas are needed and what the third antenna is for, here is the answer:
Yes, you need at least both antennas for the nRF24's! Why? To have it working on a decent range!
The average range with standard known chinese 2.4GHz antennas is about 20-30meters. Upgrading those antennas will help a lot with getting more range!

2 antennas are for the HSPI and VSPI nRF24 modules!

The 3rd antenna is plugged to the ESP32 chip itself, whether via IPEX or soldered onto its own antenna, if your ESP32 does not provide any option to add that one, it obviously won't be possible!
What is the 3rd antenna used for? The third antenna connected to the ESP32 chip itself helps with reliable long-range interference. It ensures a better intermediate signal and stability when jamming!
(The third antenna is your own decision and therefore optional!)



## Flashing the firmware
### via webflasher (Easy)                                                                
I've created a webflasher to make it super easy for you to flash your ESP32 chip with the ESP32-BlueJammer firmware of your choice!  
- Visit [ESP32-BlueJammerFlasher](https://esp32-bluejammerflasher.pages.dev)
- First, choose the firmware type, "Generic" or "0.96" OLED"
- choose the firmware you want to flash
- Connect your ESP32 via a data USB cable
- Flash the firmware of your choice :D

### Flashing ESP32 via binary files (Advanced)  
- Download the **.bin files** available on this repository
- Use any flasher of your choice
- Flash it :D

If your ESP32 is not showing up in the device list or won't get recognized you will need to have [THESE DRIVERS INSTALLED](https://www.silabs.com/documents/public/software/CP210x_Windows_Drivers.zip) which can be found on my [Discord server](https://discord.gg/yNGhKxzqUE) too!


## ESP32-nRF24L01+ pinout + battery mod
Here are both pinouts for HSPI and VSPI. You need both nRF24L01 modules connected in order to achieve full capability of the device.                
![nRF24L01+ pinout](https://dwdwpld.pages.dev/nRF24L01pinout.png)

![ESP32 32U pinout](https://ae01.alicdn.com/kf/Hcee76bca3fb64ac99cabf805925647963.png)
### HSPI
| 1st nRF24L01 module Pin | HSPI Pin (ESP32) | 10uf capacitor |
|---------------|------------------|--------------------|
| VCC           | 3.3V             | (+) capacitor |
| GND           | GND              | (-) capacitor |
| CE            | GPIO 16          |
| CSN           | GPIO 15          |
| SCK           | GPIO 14          |
| MOSI          | GPIO 13          |
| MISO          | GPIO 12          |
| IRQ           |                  |

### VSPI 
| 2nd nRF24L01 module Pin | VSPI Pin (ESP32) | 10uf capacitor |
|---------------|------------------|--------------------|
| VCC           | 3.3V             | (+) capacitor |
| GND           | GND              | (-) capacitor |
| CE            | GPIO 22          |
| CSN           | GPIO 21          |
| SCK           | GPIO 18          |
| MOSI          | GPIO 23          |
| MISO          | GPIO 19          |
| IRQ           |                  |

### Status LED
| ESP32 | 1.0k Ohm Resistor | 3mm Status LED (blue)|
|-------|-------------------|----------------------|
|  GND  |                   |       (-) LED        |
|       |      Resistor     |       (+) LED        |
|GPIO27 |      Resistor     |                      |

### OLED Display I2C (additional - make sure to use the correct firmware!)
| 0.96" OLED Display I2C | ESP32 |
|------------------------|-------|
|          GND           |  GND  |
|          VCC           | 3.3V  |
|          SCL           |GPIO 5 |
|          SDA           |GPIO 4 |

### Battery modification (additional)
| 3.7V Li-Ion battery | JST-PH2 connector    | TP4056 Charging Module | Mini Slide Switch | ESP32 |
|---------------------|----------------------|------------------------|-------------------|-------|
| (+) Battery         | (+) JST-PH2          | Bat +                  |                   |       |
| (-) Battery         | (-) JST-PH2          | Bat -                  |                   |       |
|                     |                      | OUT +                  | Switch in         |       |
|                     |                      | OUT -                  |                   |  GND  |
|                     |                      |                        | Switch out        |  3V3  |



## PCB

<h3 align="center">That's how the components are placed (PCB size=7cm x 5.5cm - Larger sizes will NOT fit in the case!)</h3>

![DIYPCB](https://dwdwpld.pages.dev/DIYPCB.jpg)



## 3D printed case
#### The 3D printed case fits ONLY a PCB size of 7cm x 5.5cm and you'll need to drill out 2 holes according for the M3 screws to fit through the PCB!
<h3 align="center">Access to the ESP32 micro-USB port, as well as to both EN & Boot buttons</h3>

![ESP32MicroUSB](https://dwdwpld.pages.dev/ESP32-BlueJammerMicroUsb.jpg)

<h3 align="center">TP4056 charging port access with charging state indicator holes (red=charging - blue=fully charged)</h3>

![USB_C_chargerWithIndicators](https://dwdwpld.pages.dev/ESP32-BlueJammerUSB_C_chargerWithIndicators.jpg)

<h3 align="center">On/off switch with blue indicator LED</h3>

![OnOffSwitch](https://dwdwpld.pages.dev/ESP32-BlueJammerOnOffSwitch.jpg)



## V3-Case 3D model view [[download .stl](https://dwdwpld.pages.dev/V3-ESP32-BlueJammerBy@emensta3DCase.stl)]

<h3 align="center">Here's a look at the V3 2 antenna version itself</h3>

![3DCaseView](https://dwdwpld.pages.dev/V3-ESP32-BlueJammer3DCaseView.png)



## V4-Case 3D model view [[download .stl](https://dwdwpld.pages.dev/V4-ESP32-BlueJammerBy@emensta3DCase.stl)]

<h3 align="center">Here's a look at the V4 3 antenna version itself</h3>

![3DCaseView](https://dwdwpld.pages.dev/V4-ESP32-BlueJammer3DCaseView.png)


<h1 align="center"> DISCLAIMER </h1>

<h4 align="center">Please note that the use of this tool is entirely at your own risk. It is intended strictly for educational purposes and should not be used for any illegal or unethical activities. Jamming is illegal and can get you in big trouble!</h4>
<h4 align="center">I'm not responsible for your actions! </h4>
