Challenge #1 - NMEA 2000 reader
=====

NMEA 2000 aka N2k is a communications standard used for connecting marine sensors and display units within ships and boats via CAN bus.

Task
-----
Given a sample N2k log that is replayed on CAN bus interface, create a Linux C++ program that reads N2k messages from that interface, keeps the state of those messages, and outputs the state in human readable form to stdout at 1 Hz.

For simplicity, read/handle not more than two messages (e.g. 128259 - Speed, Water Referenced and 127250 - Vessel Heading).

Example of state output:
```json
{"vesselHeading":{"heading":0.5, "reference": "true"}}
```

Input
-----
 - N2k sample log from [canboat](https://github.com/canboat/canboat) project [candumpSample3.txt](https://github.com/canboat/canboat/blob/master/samples/candumpSample3.txt)

Details and Hints
-----
 - Use vcan to create virtual can interface (SocketCAN) on Linux
 - NMEA 2000 network uses 250kbit/s rate i.e. 250000 bitrate
 - C++ up to v20 accepted
 - Since N2k is a closed standard, use the great open source [NMEA2000](https://github.com/ttlappalainen/NMEA2000) library to parse CAN frames into N2k messages, without having to worry about standard's particulars. The library has solid examples. Make sure to avoid compiling Arduino specific files, you'll discover those from compile errors. Easiest is to include the library source in same compilation unit with your program instead of trying to use it as a library object.
 - Use [NMEA2000_socketCAN](https://github.com/thomasonw/NMEA2000_socketCAN) library to interface NMEA2000 library with SocketCAN driver
 - Use can-utils programs (canplayer, candump) to play logs and test CAN interface
   - `canplayer -I canboat/samples/candumpSample3.txt vcan0=slcan0 -l i` replays sample log in a loop to vcan0 virtual CAN interface
   - `candump vcan0` outputs frames from vcan0 virtual CAN interface

 Deliverable
 -----
 Url to video demonstrating the results of your program,
 e.g.
  - one terminal with canplayer command that plays N2k log into vcan
  - second terminal with your program that is performing the task required
