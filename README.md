# VK Boards

Arduino Renesas Core based package containing definitions for Vekatech's Custom Arduino boards.

## Supported Boards

### ![Platform](https://img.shields.io/badge/MCU-RA4M1-green)
- VK NANO R4 (works with the original Arduino **`NANO R4`** bootloader (**`dfu_nano.hex`**))

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
  pinMode(LEDR, OUTPUT);
  pinMode(LEDG, OUTPUT);
  pinMode(LEDB, OUTPUT);
}

void loop() {
  digitalWrite(LEDB, LOW);
  digitalWrite(LEDR, HIGH);
  delay(500);
  digitalWrite(LEDR, LOW);
  digitalWrite(LEDG, HIGH);
  delay(500);
  digitalWrite(LEDG, LOW);
  digitalWrite(LEDB, HIGH);
  delay(500);
}
```
