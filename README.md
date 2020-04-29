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

![UI](images/nws_warnings.png?raw=true "NWS Warnings")
![UI](images/nws_warnings_attributes.png?raw=true "NWS Warnings Attributes")

# Current Monitors and Severitys
- Severe Thunderstorm Warning
- Tornado Watch
- Tornado Warning
- Winter Storm Warning

# Example Template Sensors / Customizations
TBD

# Example Automations
```
        ##########################################################
        ## Tornado Warning
        ##########################################################

- alias: Weather - Tornado Warning

  trigger:
    - platform: state
      entity_id: sensor.nws_tornado_warning
      from: "0"
      to: "1"

  action:
    - service: notify.mobile_app_USER1_iphone
      data:
       title: "Tornado Warning"
       message: "NWS -- {{ states.sensor.nws_warnings.attributes.tornado_warning_headline }}"
       data:
         push:
           sound:
             name: default
             critical: 1
             volume: 1.0
             
```
