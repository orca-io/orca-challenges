Challenge - canplayer frame rate mod
=====

[canplayer](https://github.com/linux-can/can-utils/blob/master/canplayer.c) is a Linux program written in C, used for replaying CAN logs to CAN interfaces. It's part of [can-utils](https://github.com/linux-can/can-utils) - a SocketCAN userspace utilities and tools package.

Task
-----
Modify [canplayer.c](https://github.com/linux-can/can-utils/blob/master/canplayer.c) to add `r` flag that defines at what frame rate (frames/second) the input log gets replayed on a CAN interface.

Example usage:
`canplayer -I sample.log vcan0=can0 -l i -r 750` to output the log at 750 f/s rate

Input
-----
 - N2k sample log from [canboat](https://github.com/canboat/canboat) project [candumpSample3.txt](https://github.com/canboat/canboat/blob/master/samples/candumpSample3.txt)
 - or any other canplayer-able log

Details and Hints
-----
 - Use vcan to create virtual can interface (SocketCAN) on Linux
 - Use candump and pv to test output rate
   - `candump vcan0 | pv -l -r > /dev/null` should tell CAN input frame rate
 - The usual way to solve this task is to introduce a delay between frames based on processing time of a frame and desired frame rate. This solution is acceptable for high performance hosts where costs to calculating necessary delays is cheap and insignificant. However, on a more limited host the delay calculation(s) may introduce additional delay which can have significant impact on output rate, so **your solution should dynamically adjust delays based on realized vs target frame rate**.

Deliverable
-----
Url to video demonstrating the results of your program
e.g.
- one terminal with canplayer command that plays a log at some specified frame rate
- second terminal that shows matching frame rate using candump and pv
- demonstrate with few different rate values
