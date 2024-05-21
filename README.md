# MicroPython on ESP32

## Install MicroPython on ESP32

1. Install esptool.py

pip install esptool

2. Connect ESP32 to PC and check COM port number

3. Erase flash

Open command prompt or terminal and run the following command to erase the flash memory of the ESP32. Replace COM13 with the actual COM port number.
```python
esptool.py --chip esp32 --port COM13 erase_flash # Local cmd
python -m esptool --port COM13 erase_flash # Global cmd
```

4. Download MicroPython firmware

Replace COM13 with the actual COM port number and ESP32_GENERIC-20240222-v1.22.2.bin with the actual MicroPython firmware file name.
```python
esptool.py --chip esp32 --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin    # Local cmd
python -m esptool --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin  # Global cmd
```

5. Reset ESP32

Press the reset button on the ESP32 board.

6. Done!

You can now use putty.exe to connect to the ESP32 and run MicroPython via the REPL (Read-Evaluate-Print-Loop) or run scripts on ESP32.

## Run MicroPython on ESP32 with vscode

1. Install node.js and Visual Studio Code:
https://nodejs.org/en/download/prebuilt-installer
(Restart Vscode after node.js installation)

2. Install pymakr extension in Visual Studio Code

3. Connect ESP32 to PC and check COM port number

4. Open Visual Studio Code and create new project in pymakr extension

5. Connect device

6. Synch project to device

```python
import sys
import time

def main():
    print("MicroPython program is running ")
    time.sleep(0.5)

if __name__=="__main__":
  print("{} initialized".format(sys.platform))
  while(1):
    try:
      main()
    except KeyboardInterrupt:
      print("Program stopped")
      sys.exit(0)
```

7. Reset ESP32 to watch output in terminal

8. Done!