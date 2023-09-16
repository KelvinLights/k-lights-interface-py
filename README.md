# k-lights-interface-py

Kelvin provides a python package called k-lights-interface to interface with Kelvin lights using bluetooth or usb (serial). This package is available on PyPI and can be installed with pip.

    pip install k-lights-interface

## Interface overview
Light | Usb    | Bluetooth |
------ | -------- | ------- |
Play and Play Pro| Yes  | Yes    |
Epos 600| Yes | Yes     |
Epos 300| No   | Yes    |
 

## Features

- Control Kelvin devices. Set brightness, CCT and Duv, RGB, HSI, read out temperatures, voltages, and more. 
- Supports Usb (serial) communication using the pyserial package
- Experimental support of BLE communication using the bleak package. Check bleak for hardware requirements.

## Usage

### Logging
Set your desired log level using the set_log_level function

```python
from k_lights_interface.k_logging import set_log_level
set_log_level(logging.NOTSET)
```
### Serial usage:

```python
from k_lights_interface.k_serial_manager import KSerialManager

dev_manager = KSerialManager()
devices = dev_manager.connect_to_all()
[print(dev) for dev in devices]
```

### BLE usage:

```python
import asyncio
from k_lights_interface.k_ble_manager import KBleManager


ble_manager = KBleManager()
devices = await ble_manager.connect_to_all()
if len(devices) == 0:
     print("No devices found")
     return
print(devices)
ret, device_stats = devices[0].get_device_stats()
print(device_stats)
```



## Issues and bugs
Please report any issues or bugs using the issues tab in this github repository.
