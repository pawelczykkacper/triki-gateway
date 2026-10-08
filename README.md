# triki-gateway
BLE gateway for Home Assistant

using information from [https://github.com/Maku-hub/TrikiScope](https://github.com/Maku-hub/TrikiScope) and ESPHome libraries and Cursor IDE with Grok 4.6 Medium create yaml configuration for ESP32 as BLE Gateway dedicated for actions and gesture from Żabka Triki to make some actions in Home Assistant

Compatbile devices:
  - all ESP32 boards with BLE support (ESP32-S2 not supported BLE connections)

> [!IMPORTANT]
> Now gateway supports a lot of sensors, but not all are useful. Work ongoing for future realeases functionality fill be improving

Fulfill mac address of Triki device. You can use on Linux terminal ```hcitool scan``` or use ```hciconfig``` or Android https://play.google.com/store/apps/details?id=com.codeweavers.bluetoothmacaddressfinder

```triki_mac: "XX:XX:XX:XX:XX:XX"```


Remember fulfill wifi credentials:  

```ssid: !secret wifi_ssid```

```password: !secret wifi_password```

or

```ssid: "NetworkName"```

```password: "NetworkPassword"```

Additional you need to add Automation on Home Assistant:
```triggers:
  - trigger: event
    event_type: esphome.triki_gesture
conditions:
  - condition: template
    value_template: "{{ trigger.event.data.gesture == 'shake' }}"

