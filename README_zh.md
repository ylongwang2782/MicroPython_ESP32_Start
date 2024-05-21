# MicroPython on ESP32 with VScode

[English](/README.md)

## 在ESP32上安装MicroPython

1. 安装 esptool.py

打开控制台或终端，并运行以下命令安装 esptool.py 工具。
```python
pip install esptool
```
2. 连接ESP32到PC并检查COM端口号

3. 擦除ESP32的flash

打开控制台或终端，并运行以下命令擦除ESP32的flash。将COM13替换为实际的COM端口号。
```python
esptool.py --chip esp32 --port COM13 erase_flash # Local cmd
python -m esptool --port COM13 erase_flash # Global cmd
```

4. 下载MicroPython固件

从以下链接下载适合你的ESP32板型的MicroPython固件。
https://micropython.org/download/

对于我来说，我下载了通用ESP32 / WROOM的固件：https://micropython.org/download/ESP32_GENERIC/

打开控制台或终端，并运行以下命令下载MicroPython固件到ESP32。将COM13替换为实际的COM端口号，ESP32_GENERIC-20240222-v1.22.2.bin替换为实际的MicroPython固件文件名。

```python
esptool.py --chip esp32 --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin    # Local cmd
python -m esptool --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin  # Global cmd
```

替换COM13为实际的COM端口号，ESP32_GENERIC-20240222-v1.22.2.bin替换为实际的MicroPython固件文件名。

5. 复位 ESP32

按下复位键（RST）重新启动ESP32。

6. 完成!

ESP32现在已经完成了MicroPython固件的下载。

## 使用VScode开发MicroPython程序

1. 安装[node.js](https://nodejs.org/en/download/prebuilt-installer)和Visual Studio Code。
（注意：如果安装过程中遇到问题，请先卸载现有的node.js和Visual Studio Code，然后重新安装）

2. 安装pymkr插件。

3. 连接ESP32到PC并检查COM端口号。

4. 打开Visual Studio Code并在pymkr插件中新建项目。

5. 在pymkr插件中连接ESP32。

6. 将示例项目同步到ESP32。

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

7. 复位ESP32以查看输出。

8. 完成！现在可以用Visual Studio Code编辑和运行MicroPython程序了。
