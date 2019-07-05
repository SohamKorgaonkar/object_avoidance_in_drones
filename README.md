## Object Avoidance in drones using any type of sensor.

**Introduction**
Currently Ardupilot supports only a certain types of sensors to be used for object avoidance. This project hopes to achieve the same using any type of sensor.

**⚠️ The  Scripts in this project are highly experimental and can lead to crash of your drone so use these with caution.**

**Requirements**

 - A Pixhwak, APM or any Ardupilot compitable flight controller.
 - A Raspberry Pi configured as a companion computer
 For more info on how to configure Raspberry Pi as a companion computer go to this link [http://ardupilot.org/dev/docs/raspberry-pi-via-mavlink.html](http://ardupilot.org/dev/docs/raspberry-pi-via-mavlink.html)

 - Basic knowledge of python.

 **Usage**
 - Copy the object_avoidance_test.py file to the Raspberry Pi.
 - Change the ECHO and TRIG pin if required.
 - Check if the serial port is correct.
 - Open Full Parameter List in mission planner and change PRX_TYPE to 2

 **Testing**

To check if everything works, connect the flight controller to mission planner.
Press Ctrl+F and select proximity
![](http://ardupilot.org/dev/_images/code-overview-object-avoidance4.png)
If obstacles are detected than everything is working fine.

**Working**

This script converts the distance measured by any sensor and converts it into a distance_sensor mavlink message and sends it to the FC via the telemetry port.
For more info [http://ardupilot.org/dev/docs/code-overview-object-avoidance.html](http://ardupilot.org/dev/docs/code-overview-object-avoidance.html)
The function sensor_data(d,o)  encodes distance and orientation as mavlink message and sends them to the fc.
The argument distance takes values in **cm** and orientation takes value as following:
0:Forward 1:Forward-Right 2:Right 3:Back-Right 4:Back 5:Back-Left 6:Left 7:Forward-Left 24:Up 25:Down
For addition of more sensors, the distance can be collected and sent via the sensor_data function with the correct orientation.
