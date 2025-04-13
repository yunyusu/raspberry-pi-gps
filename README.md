# raspberry-pi-gps

## how to build
1. hardware linking: https://pinout.xyz/pinout/3v3_power
2. set up raspberry pi:
   - write micro SD card with Raspberry pi imager(open ssd)
   - connect to the same wifi with pi
   - cmd line:
     ssh yunyu@192.168.47.133
     Cookie931019
3. test Neo 6M gps module: https://sparklers-the-makers.github.io/blog/robotics/use-neo-6m-module-with-raspberry-pi/
   - tab*2 can jump out hint directory
   - sudo vim /boot/firmware/config.txt is correct (wrongly open something readonly use :!q to exit, and typy sudo su, then try again.)
inside:
...
[all]
dtparam=spi=on
dtoverlay=pi3-disable-bt
core_freq=250
enable_uart=1
force_turbo=1

enable_uart=1
dtoverlay=uart0
dtoverlay=disable-bt

   - copy a backup
sudo cp /boot/cmdline.txt /boot/cmdline_backup.txt

   - turn of uart by copy follows code into /boot/firmware/config.txt
dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles

   - sudo cat /dev/ttyAMA0 to get signal

4. build virsual python: https://docs.python.org/zh-tw/3.13/library/venv.html
   - run with python <file-name>.py
   - sudo su can transform to root
   - ls -l /dev/ttyAMA0* to know serial information
5. read the GPS signal: https://blog.ittraining.com.tw/2016/02/gpsgprmc.html

## Planning
1. try arduino board: https://randomnerdtutorials.com/guide-to-neo-6m-gps-module-with-arduino/
2. 
