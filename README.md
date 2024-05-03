# m5stickc-plus2-esphome

M5StickC Plus2 ESPHome Barometer

![image](https://github.com/WarC0zes/m5stickc-plus2-esphome/assets/91471397/dcce46a8-6369-465e-a72b-f2d789c6f7ba)


**Requis:**
- M5SickC Plus 2
- ENV III HAT

**Display on screen:**
- Time Date
- Pression
- Température
- Humidity
- Battery level percent
- Wifi signal percent

**Option button A:**
- 1 click: toggle display
- 2 click: toggle led

**Option button B:**
- press: ring the buzzer

**Option battery:**
- an alert with the buzzer which sounds at 20% battery remaining.

For uptime template, if you compile with esp-idf, use this code:
```
  - platform: template
    id: lite_uptime
    name: Uptime
    lambda: |-
      int seconds = (id(uptime_sec).state);
      int days = seconds / (24 * 3600);
      seconds = seconds % (24 * 3600); 
      int hours = seconds / 3600;
      seconds = seconds % 3600;
      int minutes = seconds /  60;
      seconds = seconds % 60;
      if ( days ) {
        return { (to_string(days) +"d " + to_string(hours) +"h " + to_string(minutes) +"m "+ to_string(seconds) +"s ").c_str() };
      } else if ( hours ) {
        return { (to_string(hours) +"h " + to_string(minutes) +"m "+ to_string(seconds) +"s ").c_str() };
      } else if ( minutes ) {
        return { (to_string(minutes) +"m "+ to_string(seconds) +"s ").c_str() };
      } else {
        return { (to_string(seconds) +"s ").c_str() };
      }
    icon: mdi:clock-start
    update_interval: 60s
    entity_category: "diagnostic"
```



