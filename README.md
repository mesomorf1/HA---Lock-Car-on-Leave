Automation for Walk-Away Locking in Home Assistant
-
This automation is designed for the Kia EV9, which does not natively support walk-away locking. However, it can also work with other cars that meet the following requirements:

Requirements:

* Car integration in Home Assistant
* Remote locking supported
* Android Auto / CarPlay compatibility


How does it work?
-
When Android Auto / CarPlay disconnects, the automation begins monitoring the Wi-Fi connection between your phone and the car. As you walk away from your car, your phone will lose the Wi-Fi signal, triggering the automation to lock the doors.


The Logic
-
When the car is completely turned off, the Wi-Fi connection between your phone and the car remains active for approximately 6 minutes and 55 seconds. This time frame is crucial as it defines the maximum duration for the automation to run.

The automation uses a 5-minute wait time by default. You can adjust this value, but it must not exceed 6:55 minutes. A longer duration may risk locking the car even if your phone is still inside.

Behavior:
-
Standard Operation:
The automation waits up to 5 minutes for your phone to move out of range. As soon as your phone is undetectable, the car locks.

Abort Scenario:
If your phone remains connected during the entire wait period (e.g., you left it in the car or stayed close by), the automation cancels itself and does not lock the car.


FAQ:
-

Q: What happens if my phone runs out of battery or I turn it off?

A: The car will not lock because the automation requires an "away" signal from your phone. If no signal is sent, the automation aborts.

---

Q: Can I set the wait time above 6:55 minutes?

A: No, 6:55 minutes is the maximum time the car's Wi-Fi remains active after shutting down. This value was tested on my setup and may vary slightly with different configurations.

---

The Setup:
-
* You need the Home Assistent app in your phone
* You need to turn on the sensor for Android Auto / CarPlay in System -> App -> Manage Sensors
* Create the automation using the YAML code in this project
* Edit the placeholders (see instructions below)


Placeholder Guide
-
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


Warning
-
⚠️ Test Before Using

This automation should be tested at home or in a safe environment before relying on it. While it works flawlessly for me (tested only on a Samsung phone), I cannot guarantee the same results for other setups.

Let me know if you'd like any additional adjustments or clarifications! 😊
