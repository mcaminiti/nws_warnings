# National Weather Service (NWS) Warnings for Home Assistant
Home Assistant Custom Component for National Weather Service Warnings

# Installation
1. Place folder (nws_warnings) in custom_components folder

# Configuration
1. Lookup Zone or County Code on NWS site https://www.weather.gov/lsx/
- Type in City and State and perform a lookup.  Scroll down and pick "ZONE AREA FORCAST FOR XXXXXX COUNTY".  
- ZoneID will be displayed in the URL
2. Add configuration to Home Assistant sensors.yaml or configuration as a sensor
```
### WEATHER SERVICE Sensors
  - platform: nws_warnings
    zone_id: 'XXXXXX'
```

# Sensors Activated
NWS Warnings will show a total count of alerts present for your county / zone.


