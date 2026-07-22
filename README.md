# VK Boards

Arduino Renesas Core based package containing definitions for Vekatech's Custom Arduino boards.

## Supported Boards

### ![Platform](https://img.shields.io/badge/MCU-RA4M1-green)
- VK NANO R4 (works with the original Arduino **`NANO R4`** bootloader (**`dfu_nano.hex`**))
### ![Platform](https://img.shields.io/badge/MCU-RA4M2-green)
- VK-RA4M2_NANO (new board for the Arduino Renesas Core, works with own dedicated bootloader (**`dfu_vk-ra4m2-nano.hex`**))
- VK-RA4M2-FEMTO (new board for the Arduino Renesas Core, works with own dedicated bootloader (**`dfu_vk-ra4m2-femto.hex`**))
### ![Platform](https://img.shields.io/badge/MCU-RA6M3-green)
- Comming soon
### ![Platform](https://img.shields.io/badge/MCU-RA6M5-green)
- Comming soon

## Installation

### ![Arduino IDE](https://img.shields.io/badge/Arduino_IDE-2.x-00979D)

1. Open **File → Preferences**
2. In **Additional Boards Manager URLs**, add:

```text
https://raw.githubusercontent.com/Vekatech/Arduino/main/package_vekatech_index.json
```

3. Open **Tools → Board → Boards Manager**
4. Search for:

```text
VK Boards
```

5. Click **Install**

### Select the Board

After installation:

```text
Tools → Board → VK Boards → VK NANO R4
```

## Uploading

Connect the board via USB and upload your sketch normally using:

```text
Sketch → Upload
```

## Example

```cpp
void setup() {
#if defined(ARDUINO_VK_NANO_R4)
  pinMode(LEDR, OUTPUT);
  pinMode(LEDG, OUTPUT);
  pinMode(LEDB, OUTPUT);
#elif defined(ARDUINO_VK_RA4M2_NANO)
  pinMode(LED_USER, OUTPUT);
  pinMode(LED_BUILTIN, OUTPUT);
#elif defined(ARDUINO_VK_RA4M2_FEMTO)
  pinMode(LED_BUILTIN, OUTPUT);
#else
#error Unsupported board!
#endif
}

void loop() {
#if defined(ARDUINO_VK_NANO_R4)
  digitalWrite(LEDB, LOW);
  digitalWrite(LEDR, HIGH);
  delay(100);
  digitalWrite(LEDR, LOW);
  digitalWrite(LEDG, HIGH);
  delay(100);
  digitalWrite(LEDG, LOW);
  digitalWrite(LEDB, HIGH);
  delay(100);
#elif defined(ARDUINO_VK_RA4M2_NANO)
  digitalWrite(LED_USER, LOW);
  digitalWrite(LED_BUILTIN, HIGH);
  delay(100);
  digitalWrite(LED_BUILTIN, LOW);
  digitalWrite(LED_USER, HIGH); 
  delay(100);
#elif defined(ARDUINO_VK_RA4M2_FEMTO)
  digitalWrite(LED_BUILTIN, LOW);
  delay(100);
  digitalWrite(LED_BUILTIN, HIGH);
  delay(100);
#endif
}
```
