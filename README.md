Automation for Walk-Away Locking in Home Assistant (Kia EV9)

This automation is designed for the Kia EV9, which does not natively support walk-away locking. However, it can also work with other cars that meet the following requirements:
Requirements:

    Integration in Home Assistant
    Remote Locking Support
    Android Auto / CarPlay Compatibility

Placeholder Guide

You will need to replace the placeholders (marked with [ ]) in the automation with your specific details:

    [PHONE_CONNECTED_SENSOR]
        Description: Your entity for Android Auto or CarPlay connection.
        Example: binary_sensor.your_phone_android_auto.

    [PHONE_WIFI_BSSID_SENSOR]
        Description: The entity for your phone's WiFi sensor.
        Example: sensor.your_phone_wifi_bssid.

    [CAR MAC ADDRESS]
        Description: Your car's WiFi (ad-hoc) MAC address.
        Details: You can find this in Home Assistant as a sensor, representing the network your phone connects to while in the car.
        Format: xx:xx:xx:xx:xx:xx.

    [LOCK_DEVICE_ID]
        Description: The ID of your car in Home Assistant.
        Example: a71b9e22db3917477a6837c7a06d90bb.

    [CAR_DOOR_LOCK_ENTITY]
        Description: The entity ID for the "Lock" command of your car.
        Example: lock.car_door_lock.
