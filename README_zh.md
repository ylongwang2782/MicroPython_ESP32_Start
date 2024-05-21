# MicroPython on ESP32 with VScode

[English](/README.md)

## ��ESP32�ϰ�װMicroPython

1. ��װ esptool.py

�򿪿���̨���նˣ��������������װ esptool.py ���ߡ�
```python
pip install esptool
```
2. ����ESP32��PC�����COM�˿ں�

3. ����ESP32��flash

�򿪿���̨���նˣ������������������ESP32��flash����COM13�滻Ϊʵ�ʵ�COM�˿ںš�
```python
esptool.py --chip esp32 --port COM13 erase_flash # Local cmd
python -m esptool --port COM13 erase_flash # Global cmd
```

4. ����MicroPython�̼�

���������������ʺ����ESP32���͵�MicroPython�̼���
https://micropython.org/download/

��������˵����������ͨ��ESP32 / WROOM�Ĺ̼���https://micropython.org/download/ESP32_GENERIC/

�򿪿���̨���նˣ�������������������MicroPython�̼���ESP32����COM13�滻Ϊʵ�ʵ�COM�˿ںţ�ESP32_GENERIC-20240222-v1.22.2.bin�滻Ϊʵ�ʵ�MicroPython�̼��ļ�����

```python
esptool.py --chip esp32 --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin    # Local cmd
python -m esptool --port COM13 --baud 460800 write_flash -z 0x1000 ESP32_GENERIC-20240222-v1.22.2.bin  # Global cmd
```

�滻COM13Ϊʵ�ʵ�COM�˿ںţ�ESP32_GENERIC-20240222-v1.22.2.bin�滻Ϊʵ�ʵ�MicroPython�̼��ļ�����

5. ��λ ESP32

���¸�λ����RST����������ESP32��

6. ���!

ESP32�����Ѿ������MicroPython�̼������ء�

## ʹ��VScode����MicroPython����

1. ��װ[node.js](https://nodejs.org/en/download/prebuilt-installer)��Visual Studio Code��
��ע�⣺�����װ�������������⣬����ж�����е�node.js��Visual Studio Code��Ȼ�����°�װ��

2. ��װpymkr�����

3. ����ESP32��PC�����COM�˿ںš�

4. ��Visual Studio Code����pymkr������½���Ŀ��

5. ��pymkr���������ESP32��

6. ��ʾ����Ŀͬ����ESP32��

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

7. ��λESP32�Բ鿴�����

8. ��ɣ����ڿ�����Visual Studio Code�༭������MicroPython�����ˡ�
