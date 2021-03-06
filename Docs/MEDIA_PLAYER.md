<p align="center">
  <a href="#"><img src="http://www.tooltip.gr/github_assets/smartir_mediaplayer.png" width="350" alt="SmartIR Media Player"></a>
</p>

## Installation:
Create a new folder into the Home Assistant's `custom_components` folder and name it `smartir`. Copy `__init__.py` and `media_player.py` into the `smartir` folder. ~~Create the subfolders `codes/media_player` into the `smartir` folder and copy the code file for your device.~~ In the last version, the component creates the `codes/media_player` subfolders if they not exist.

## Configuration variables:
**name** (Optional): Name to use in the frontend<br />
**device_code** (Required): ...... (Accepts only positive numbers)<br />
**controller_send_service** (Required): The service that will be used to send the commands. Only `broadlink_send_packet` (Broadlink controller) is currently supported.<br />
**power_sensor** (Optional): *entity_id* for a sensor that monitors whether your device is actually On or Off. This may be a power monitor sensor. (Accepts only on/off states)<br />

## Example (using broadlink controller):
```yaml
switch:
  - platform: broadlink
    host: 192.168.10.10
    mac: '00:00:00:00:00:00'
    
media_player:
  - platform: smartir
    name: Living room TV
    device_code: 1000
    controller_send_service: switch.broadlink_send_packet_192_168_10_10
    power_sensor: binary_sensor.tv_power
```

## Available codes for TV devices:
Below are the code files created by the people in the community. Before you start creating your own code file, try if one of them works for your device. **Please open an issue if your device is working and not included in the supported models.**

#### Philips
| Code | Supported Models | Controller |
| ------------- | -------------------------- | ------------- |
[1000](../smartir/codes/media_player/1000.json)|Unknown|Broadlink

#### Sony
| Code | Supported Models | Controller |
| ------------- | -------------------------- | ------------- |
[1020](../smartir/codes/media_player/1020.json)|KDL-46HX800|Broadlink

#### LG
| Code | Supported Models | Controller |
| ------------- | -------------------------- | ------------- |
[1040](../smartir/codes/media_player/1040.json)|22MT47DC|Broadlink
