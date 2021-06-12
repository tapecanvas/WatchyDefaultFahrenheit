# WatchyDefaultFahrenheit
instructions to set the default 7seg watch face's weather info to your location and change temperature display to fahrenheit.

1. First find where your arduino sketchbook folder is located. For example: mine is Documents/Arduino.
2. Enter the arduino folder and then enter the "libraries" folder.
3. Find the "Watchy" folder then enter into the "src" folder.
4. Open the file "config.h" in a text editor such as Atom, VisualStudio, notepad, etc..
5. On line 28 (#define CITY_NAME "NEW+YORK"), replace "NEW+YORK" with your city's name. If your city has a space between words use the "+" in its place.
6. Change line 29 to your country's code if needed.

7. Next, go to https://home.openweathermap.org/users/sign_up and create a free account.
8. Create a new api key and copy the generated key.
9. Back in the "config.h" file from above, on line 30, replace the default key with the one you just generated.
10. On line 31, insert your city name and api key like so: (#define OPENWEATHERMAP_URL "http://api.openweathermap.org/data/2.5/weather?q={yourcityname}&appid={yourapikey}"
11. On line 32, change metric to imperial (#define TEMP_UNIT "imperial" //use "imperial" for Fahrenheit"

12. Now open Arduino program and go to file/examples/Watchy/WatchFaces/7_SEG
13. Select the "Watchy_7_SEG.cpp tab
14. Scroll down to line 107 and change "metric" to "imperial" and ==0 ? to ==1 ?
15. To finish, click the checkmark in the top left to compile the code (this can take a minute)
16. The output console should read:
WARNING: library DS3232RTC claims to run on avr architecture(s) and may be incompatible with your current board which runs on esp32 architecture(s).
Sketch uses 1783902 bytes (90%) of program storage space. Maximum is 1966080 bytes.
Global variables use 58392 bytes (17%) of dynamic memory, leaving 269288 bytes for local variables. Maximum is 327680 bytes.--------------------------Compilation complete.
17. Connect your Watchy to your computer using a usb data cable. [data vs charge](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/)
18. Hit the upload button and wait for the watchy to reboot. Your temperature should now be accurate to your locale and in degrees F.

