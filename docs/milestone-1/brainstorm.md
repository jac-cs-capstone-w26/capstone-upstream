**Purpose**

This project is a smart locker security system that monitors and protects a physical locker using IoT-connected sensors and a mobile app. The system detects unauthorized access attempts, including door breaches, proximity, and physical tampering, and sends real-time alerts to the owner. All event data is streamed to Azure IoT Central, giving users a full audit log of locker activity accessible from anywhere.

---

**Subsystem 1: Intrusion Detection**

This subsystem is responsible for detecting unauthorized physical access to the locker. It monitors the door state and surrounding motion, acting as the primary trigger for alerts across the rest of the system.

| Component | Interface | Documentation |
| --- | --- | --- |
| Magnetic Door Sensor (Reed Switch) | Digital | https://abra-electronics.com/electromechanical/switches/magnetic-reed-switches/sec-100-magnetic-door-sensor-no.html |
| PIR Motion Sensor | Digital | https://wiki.seeedstudio.com/Grove-Adjustable_PIR_Motion_Sensor/ |
| Built-in Buzzer | I2C | https://wiki.seeedstudio.com/reTerminal-hardware-interfaces-usage/#buzzer |

---

**Subsystem 2: Tamper and Status Feedback**

This subsystem monitors for physical tampering with the locker itself and provides immediate visual feedback on the locker's current security state. It complements the intrusion detection subsystem by catching attacks that don't involve the door directly, such as hitting or shaking the locker.

| Component | Interface | Documentation |
| --- | --- | --- |
| Built-in Accelerometer | I2C | https://wiki.seeedstudio.com/reTerminal-hardware-interfaces-usage/#accelerometer |
| RGB LED Stick | PWM | https://wiki.seeedstudio.com/Grove-RGB_LED_Stick-10-WS2813_Mini/ |
| MG90S Micro Servo (lock actuator) | PWM | https://abra-electronics.com/electromechanical/motors/servo-motors/mg90s-metal-gear-micro-servo-rc-micro-servo.html |

---

**Subsystem 3: Remote Monitoring and Control**

This subsystem handles the cloud integration and mobile app interface, giving the locker owner the ability to arm/disarm the system, receive push notifications, and review a full event history from their phone. It ties the hardware subsystems together by routing telemetry through Azure IoT Central and exposing controls via the Expo app.

| Component | Interface | Documentation |
| --- | --- | --- |
| Azure IoT Central | Cloud/MQTT | https://learn.microsoft.com/en-us/azure/iot-central/ |
| Expo TypeScript App | N/A (software) | https://docs.expo.dev/ |
