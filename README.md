## Polar Coaster V2

![](http://www.buildlog.net/blog/wp-content/uploads/2019/05/20190112_182753.jpg)

This is a pen plotter designed to draw things on round drink coasters. It was primarily designed as a simple demostration project of polar kinematics.

I got a lot of requests to post the source files, so here they are. You should have a basic familiarity of how 3D printers or CNC machines work and a basic understanding of how to make gcode. I can only provide basic support via [GitHub issues](<https://github.com/bdring/Polar-Coaster/issues>).

### Source files

- Mechanicals
  - [STL Files](<https://github.com/bdring/Polar-Coaster/tree/master/mechanics/stl>)
  - [3D STEP Assembly File](<https://github.com/bdring/Polar-Coaster/tree/master/mechanics/source>)
- PCB
  - [Gerber Files](<https://github.com/bdring/Polar-Coaster/tree/master/pcb/gerber>)
  - [Source: Diptrace](<https://github.com/bdring/Polar-Coaster/tree/master/pcb/source>)
- BOM ( [work in progress](https://docs.google.com/spreadsheets/d/1ZX7-w3RRlV4LFHbHOMovw8RLWblGm1u_bLe6--jveR4/edit?usp=sharing) )

### Firmware

It currently uses a [branch of the Grbl_ESP32 firmware](<https://github.com/bdring/Grbl_Esp32/tree/Kinematic_Test>).



### Setup

[Get some coasters from Amazon](https://www.amazon.com/dp/B01H0PO19S)

After you have the frimware loaded use a serial termnial to setup the work coordinate system so the pen 0,0 is roughly near the middle and the pen is up by sending G10 L2 P0 X-43 Y-5. you only need to do this once.

**Centering (important for good quality plots)**

If the machine does not have an accurate center, lines that go near the center will get distorted.

Load a coaster by pressing onto the bed. give a little push down at each of the 6 friction grips. Home the machine by sending $H or clicking the S1 button on the machine. Move the pen carriage to the middle by sending G0 X0 Y0.   Mount a pen so that the tip just touches the coaster. Spin the coaster by hand to draw with the pen. This will give you an indication of how close the pen tip is near the center of the coaster. 

To adjust the center you can use the X axis jogging controls on the WebUI and by loosening and swiveling the arm. Be careful not to accidentally move the pen by hand. 

After you have it close, Click the the X zero button below the jog panel or sending G10 L20 P0 X0.

Verify everything is working by rehoming, sending to X0,Y0 and checking the center.

You need to do this everytime you use a new type of pen or if the plot quality does not look good.

### Usage Instructions

Load a coaster

There are three buttons. The one towrds the front is a homing button. If you click this it will home and the pen carriage will go up. Mount the pen with the tip about 2 mm above the surface.

You can stream gcode or you can put files on a micro SD card. If you name your files 1.nc or 2.nc, you can use the buttons to play those files. Button S2 = 1.nc and S3 = 2.nc.

### Issues.

1. The PCB was designed to allow the use of both 0.9" and 1.0" pitch 19x2 pin ESP32 dev modules. The wider ones tend to have an overhanging antenna section that will interfere with on of the stepper drivers. 
2. Hot Motors: Keep the current very low on the motors. If they get hot, the PLA could get damaged. I like to run TMC2130 drivers in stand alone mode. They are very quient and cool.



