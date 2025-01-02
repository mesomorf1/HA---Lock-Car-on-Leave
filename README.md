Automation for Walk-Away Locking in Home Assistant (Kia EV9)
-
This automation is designed for the Kia EV9, which does not natively support walk-away locking. However, it can also work with other cars that meet the following requirements:
Requirements:

    Integration in Home Assistant
    Remote Locking Support
    Android Auto / CarPlay Compatibility


How does it work?
-

When Android Auto / CarPlay gets disconnected the automation will start waiting for the wifi connection with the car to end. So when you start walkning away from your car your phone will start loosing signal with the car and when it does it will lock the doors.



The Logic:
-
When car is 100% turned off the wifi connection between your mobile and the car is STILL ALIVE!
I have measured it to be alive for a 6 minutes and 55 seconds.
That number is important because that will be the maximum time for the automation to live.
I have set 5 minutes as a "wait time" and you can adjust it lower or higher, but do not exeed 6:55 minutes since that will allow your car to lock itself even if your phone is in the car.

So:
As standard the automation waits up to 5 minutes for you to get away from your car so it can lock the car for you. As soon it can't detect your phone it will lock.
If it sense your phone the whole 5 minutes (perhaps your phone is left in the car or you are right next to it) then it will abort to automation and NOT lock the car.


FAQ:
-

Q: If phone runs out of battery or if I turn off the phone, will it make the car to lock? 
A: No, since it is required that the phone sends an "away" signal to Home Assistant this will not happen and the automation will abort

Q: Can I set the wait time above 6:55 minutes?
A: No, that is the max time that wifi is alive after you shutdown your car. Sidenote: I have only used this on my own phone so i can not say this for 100%


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
