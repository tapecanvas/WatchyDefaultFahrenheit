# WatchyDefaultFahrenheit
instructions to set the default 7seg watch face's weather info to your location and change temperature display to fahrenheit.

1. First find where your arduino sketchbook folder is located. For example: mine is Documents/Arduino.
2. Enter the arduino folder and then enter the "libraries" folder.
3. Find the "Watchy" folder then enter into the "src" folder.
4. Open the "Watchy.cpp" file in a text editor such as Atom, VisualStudio, notepad, etc..
5. Go to line 596 "String weatherQueryURL = String(OPENWEATHERMAP_URL) + String(CITY_NAME) + String(",") + String(COUNTRY_CODE) + String("&units=") + String(TEMP_UNIT) + String("&appid=") + String(OPENWEATHERMAP_APIKEY);"
6. Edit this line to read "String weatherQueryURL = String(OPENWEATHERMAP_URL) + String(CITY_ID) + String("&units=") + String(TEMP_UNIT) + String("&appid=") + String(OPENWEATHERMAP_APIKEY);"
7. Open the file "config.h" from the src folder.
8. Change line 28 (#define CITY_NAME "NEW+YORK"), to #define CITY_ID "5128581" //find your city id by searching your city on https://openweathermap.org/ ,your city id will appear in the address bar. Ex: https://openweathermap.org/city/5128581 <-- the number is your city id.
9. Delete line 29 that contains "country code", it is no longer needed since we have the city id.
7. Next, go to https://home.openweathermap.org/users/sign_up and create a free account.
8. Create a new api key and copy the generated key.
9. Back in the "config.h" file from above, on line 29, replace the default key with the one you just generated.
10. On line 30, edit it to read: #define OPENWEATHERMAP_URL "http://api.openweathermap.org/data/2.5/weather?id="
11. On line 31, change metric to imperial (#define TEMP_UNIT "imperial" //use "imperial" for Fahrenheit"
12. Add #define WEATHER_UPDATE_INTERVAL 30 //minutes on the next line
13. Now open Arduino program and go to file/examples/Watchy/WatchFaces/7_SEG
14. Select the "Watchy_7_SEG.cpp tab
15. Scroll down to line 107 and change "metric" to "imperial" and ==0 ? to ==1 ? //the 1 changes the C icon to an F
16. To finish, click the checkmark in the top left to compile the code (this can take a minute)
17. The output console should read: 
WARNING: library DS3232RTC claims to run on avr architecture(s) and may be incompatible with your current board which runs on esp32 architecture(s).
Sketch uses 1783902 bytes (90%) of program storage space. Maximum is 1966080 bytes.
Global variables use 58392 bytes (17%) of dynamic memory, leaving 269288 bytes for local variables. Maximum is 327680 bytes.--------------------------Compilation complete.
17. Connect your Watchy to your computer using a usb data cable. [data vs charge](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/)
18. Make sure that the correct board is selected to flash to:
19. Go to "Tools" -> Board Manager -> search for esp32 and install the latest version.
20. Return to "Tools" -> Board -> esp32 and select "ESP32 Dev Module"
21. In "Tools" go to "Partition Scheme" and select "Minimal SPIFFS"
22. Under the "Help" button in arduino you should see "ESP32 Dev Module" on the drop down menu and the usb port the Watchy is connected to. 
23. Hit the upload button and wait for the watchy to reboot. Your temperature should now be accurate to your locale and in degrees F.

Thanks to smkirchn for helping to fine tune these instructions (: If you have any problems, add an issue here, or reach out in the Watchy Discord and @tapecanvas to get my attention. Good luck!

