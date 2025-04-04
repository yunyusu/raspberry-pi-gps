# raspberry-pi-gps

## how to build
1. hardware linking: https://pinout.xyz/pinout/3v3_power
2. set up raspberry pi:
   - write micro SD card with Raspberry pi imager(open ssd)
   - connect to the same wifi with pi
   - cmd line:
     ssd user-name@ip-address
     enter password
3. test Neo 6M gps module: https://sparklers-the-makers.github.io/blog/robotics/use-neo-6m-module-with-raspberry-pi/
   - tab*2 can jump out hint directory
   - sudo nano /boot/firmware/config.txt is correct
4. build virsual python: https://docs.python.org/zh-tw/3.13/library/venv.html
   - run with python <file-name>.py
   - sudo su can transform to root
   - ls -l /dev/ttyAMA0* to know serial information
5. read the GPS signal: https://blog.ittraining.com.tw/2016/02/gpsgprmc.html
