Created this automation in Home assistant for my Kia EV9 that don´t support walk-away locking.

---

Will work for all other cars that support:
* Intergration in Home Assistant
* Remote locking
* Android Auto / Car Play

---

I have put brackets [] where you need to enter your own details like:

[PHONE_CONNECTED_SENSOR]
Info: Your entity for Android Auto / Car Play

[PHONE_WIFI_BSSID_SENSOR]
Info: Your entity for the phones wifi sensor

[CAR MAC ADDRESS]
Info: This is you cars wifi (ad-hoc) adress. You will find it in Home Assistant as a sensor (the network your phone is connected to). Format is: xx:xx:xx:xx:xx:xx

[LOCK_DEVICE_ID]
Info: The ID of your car in Home assistant

[CAR_DOOR_LOCK_ENTITY]
info: The ID for the "Lock" command of your car

---

WARNING!
Try this at home first, I can not guarantee it will work flawless for you as it does for me (only tested on Samsung phone).
