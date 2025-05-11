# raspberry-pi-gps

## how to build
1. hardware linking:
   - raspberry pi: https://pinout.xyz/pinout/3v3_power
   - RYS352A:
      1. https://www.instructables.com/Nature-Trail-Mapper-With-ESP32-and-RYS352A-GPS-Mod/
      2. https://reyax.com/products/RYS352A
   - tiny gps in arduino
        - https://vocus.cc/article/65d307b9fd8978000146360a
        - https://github.com/mikalhart/TinyGPSPlus/tree/master/examples
3. set up raspberry pi: https://reyax.com/products/RYS352A
   - write micro SD card with Raspberry pi imager(open ssd)
   - connect to the same wifi with pi
   - cmd line:
        - ssh yunyu@192.168.47.133
        - Cookie931019
4. test Neo 6M gps module: https://sparklers-the-makers.github.io/blog/robotics/use-neo-6m-module-with-raspberry-pi/
   - tab*2 can jump out hint directory
   - sudo vim /boot/firmware/config.txt is correct (wrongly open something readonly use :!q to exit, and typy sudo su, then try again.)
      - 大概就是在說要開啟Uart串口，不要使用mini Uart(該接口從mini Uart→Uart)，詳見：https://harttle.land/2017/01/14/raspberrypi-uart.html
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
4'. directly run written python code on it
   - To transfer the file from your laptop to raspberry pi
     - scp hello.py yunyu@192.168.47.133:~/
     - will see in the yunyu directory
   - To move it
     - mv filename ~/destination
   - To run the code
     - python3 filename.py 


5. read the GPS signal: https://blog.ittraining.com.tw/2016/02/gpsgprmc.html

## Planning
1. try arduino board: https://randomnerdtutorials.com/guide-to-neo-6m-gps-module-with-arduino/
2. try RYS352A and visual
3. try RTK(too expansive QQ)
4. why does it shut down all a sudden?
- 供電不穩？
=> 用pico、Arduino測試後皆不會出現狀況
5. power consumption
  p = IV (find quiescent current)

  





