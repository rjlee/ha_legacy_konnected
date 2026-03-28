# Home Assistant Konnected.io (Legacy) Custom Component

Custom Home Assistant integration for Konnected Alarm Panels and sensors.

This is a fork of the original Konnected integration that was removed from Home Assistant Core. It provides full compatibility with Konnected hardware devices still on the Konnected original firmware that haven't migrated to the newer ESPHome based firmware.

## Features

- Support for Konnected Alarm Panel (original and Pro models)
- Binary sensor support (door, window, motion, etc.)
- Temperature and humidity sensors (DHT11/DHT22)
- DS18B20 one-wire temperature sensors
- Switch/actuator control with momentary and pulse options
- YAML configuration support (legacy)
- SSDP discovery
- Config Flow setup

## Installation

### Option 1: HACS (Recommended)

1. Open HACS in Home Assistant
2. Go to Integrations
3. Click the three dots (top right)
4. Select "Custom repositories"
5. Add: `https://github.com/rjlee/ha_legacy_konnected`
6. Select category: "Integration"
7. Click "Add"
8. Find "Konnected.io (Legacy) Custom Component" and install

### Option 2: Manual

1. Copy the `ha_legacy_konnected` folder to your Home Assistant's `custom_components/` directory
2. Restart Home Assistant
3. Go to Settings > Devices & Services > Add Integration
4. Search for "Konnected.io (Legacy) Custom Component"

## Configuration

### UI Configuration (Recommended)

1. Add the integration via the Home Assistant UI
2. Follow the configuration flow to discover your Konnected devices

### YAML Configuration (Legacy)

```yaml
konnected:
  access_token: your_access_token_here
  api_host: http://homeassistant.local:8123  # optional
  devices:
    - id: your_device_id
      host: 192.168.1.100
      port: 8080
      binary_sensors:
        - zone: 1
          type: door
          name: "Front Door"
        - zone: 2
          type: motion
          name: "Living Room"
      switches:
        - zone: out
          name: "Siren"
          momentary: 1000
          pause: 1000
          repeat: 3
      sensors:
        - zone: 3
          type: dht
          name: "Garage Temperature"
          poll_interval: 3
```

## Supported Hardware

- Konnected Alarm Panel (original)
- Konnected Alarm Panel Pro

## Requirements

- Home Assistant 2024.1 or later
- Python 3.11+
- `konnected` Python package (installed automatically)

## Troubleshooting

### Device Not Discovering

Ensure your Konnected device is on the same network as Home Assistant. The integration uses SSDP/mDNS for discovery.

### Can't Add Integration

If the integration doesn't appear, try:
1. Clear your browser cache
2. Restart Home Assistant
3. Check the Home Assistant logs for errors

## Support

- Issues: https://github.com/rjlee/ha_legacy_konnected/issues
- Home Assistant Community: https://community.home-assistant.io/

## License

MIT License - See LICENSE file for details

## Acknowledgments

- Original integration by @heythisisnate
- Konnected.io for their hardware
