# DS18B20_YF-S201_RaspberryPi
This project can be use as a RaspberryPi temperature sensor(DS18B20) and water flow meter(YF-S201) example. 

## YF-S201
### Rasperry Pi pinout
2 - 5volts<br>
6 - GND<br>
8  - Data (flowmeter1)<br>
10 - Data (flowmeter2)<br>

### Run
`
$ cd YF-S201 && python main.py -pin 8
`

## DS18B20
### install
`
$ cd DS18B20/ && bash install.sh
`
<br>You can test with this command:<br>
`
$ cat /sys/bus/w1/devices/28-XXXXXXXXXXXX/w1_slave
`

### Rasperry Pi pinout
1 - 3.3volts<br>
6 - GND<br>
7 - Data<br>

### Run
`
$ cd DS18B20 && python main.py
`

## InfluxDB
### Install
`
$ cd InfluxDB/ && bash install.sh
`
<br>You should be now able to open:<br>
http://localhost:8083<br>

## Grafana
You can install Grafana via this command line:<br>
`
$ cd Grafana/ && bash install.sh
`
<br>You should be now able to open:<br>
http://localhost:3000<br>

This file is a dashboard example:<br>
`
$ cat Grafana/telemetry.json
`

## Start at boot
`
$ sudo nano /etc/rc.local
`
<br>Add lines before "exit 0":<br>
`python /home/pi/DS18B20_YF-S201_RaspberryPi/DS18B20/main.py &`<br>
`python /home/pi/DS18B20_YF-S201_RaspberryPi/YF-S201/main.py &`<br>
[more info](https://www.raspberrypi.org/documentation/linux/usage/rc-local.md)

## PiOLED
### Install
`
$ cd PiOLED/ && bash install.sh `<br>
`
-->Enable I2C interface when 'raspi-config' interface pop up.
`
<br>For testing, see examples in folder:<br>
`
$ ls Adafruit_Python_SSD1306/examples
`
