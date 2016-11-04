Playing with ESP8266...

* [Build environment setting](https://github.com/seanshpark/help/wiki/ESP8266-build-environment-setting)
* [Build JerryScript on ESP8266](https://github.com/seanshpark/help/wiki/ESP8266-JerryScript)
* [About ESP flashing tool](https://github.com/themadinventor/esptool/)
* [Memory Map](https://github.com/esp8266/esp8266-wiki/wiki/Memory-Map)
* [Erase Flash](http://www.pratikpanda.com/completely-format-erase-esp8266-flash-memory/)

While playing with ESP8266...
* WiFi is somewhat unstable. It keeps disconnected to the AP when in station mode.
* Need more try-and-error with tcp APIs. It gets unstable when sending continuous packets.

How-To
* use `minicom`, 115200-N-8-1
```
sudo minicom --device /dev/ttyUSB0
```
* `ENTER + CTRL-J` to Feed the command. Single `ENTER` won't work.

Showing Boot Log with 74880 baud
* http://sensornodeinfo.rockingdlabs.com/blog/2016/01/19/baud74880/
```
git clone https://gist.github.com/3f1a984533556cf890d9.git anybaud
cd anybaud
gcc gistfile.c -o anybaud
cp anybaud ~/bin
# run minicom, then run anybaud
anybaud /dev/ttyUSB0 74880
# don't have to run in su
```


##### Reference
* There's a [great book](http://neilkolban.com/tech/esp8266/) to read and it's free.
* Reference documents: http://bbs.espressif.com/viewtopic.php?f=51&t=1024
* https://room-15.github.io/blog/2015/03/26/esp8266-at-command-reference/
