Getting I2C and maybe GPIO's to work?

May need to flash OLDER jetpack to get jetson_io working...

Looks like 4.3 may have some later videos with my old Youtube guy

-- Software get ability to i2c control

sudo pip3 install adafruit-circuitpython-servokit
sudo usermod -aG i2c bubba
sudo groupadd -f -r gpio
sudo usermod -a -G gpio bubba
sudo cp /opt/nvidia/jetston-gpio/etc/99-gpio.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules && sudo udevadm trigger
sudo reboot now
---
sudo i2cdetect -y -r 1
  look for 40 in column 0 of row 40
  and also 70 in column 0 of row 70
  
  
create python prog
from adafruit_servokit import ServoKit
myKit=ServoKit(channels=16)


