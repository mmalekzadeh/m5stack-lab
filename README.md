# M5Stack-Lab
A tutorial on how to get your hands dirty on the combination of M5stack, Arduino, and Jupyter Notebook. 
```
This tutorial is originally created for the Ambient Sensing Lab (Sensing and IOT module) at Imperial College Faculty of Engineering.
```
## (1) What is the M5Stack and what can it be used for?

The M5Stack is essentially a ESP32 development board, which comes with a screen, microphone and other features built-in, which makes it programmable through the Arduino IDE, yet modular and easy to use.
You can program the M5Stack to become a clock, timer, GPS, Accelerometer, Gyroscope, Microphone/Recorder, MP3 Player, Temperature sensor (or regulator), Voice-Initiated Light Switch, and many more things. It is intended to turn your idea into a prototype product with a simple code. 
In this tutorial you will learn how to collect and use the M5Stack built in Gyro and Accelerometer and Temperature sensor data to complete time series data analyses.

### How to get started?

After you get an M5Stack, you may want to program it. NOTE: Programming an M5Stack via the Arduino IDE will delete the factory set code, however you will still be able to reprogram it with the firmware at a later stage.

### Step 1

Firstly, download the Arduino IDE from https://www.arduino.cc/en/Main/Software.

### Step 2

Secondly, download the M5Stack Library and IDF from www.m5stack.com

  **A. For MacOS:**
  
  https://m5stack.readthedocs.io/en/latest/get-started/m5stack_core_get_started_Arduino_MacOS.html
  
  Note: you should go all the way through It and do all the installations :
  
  1)	Setting Environment
  
  2)	ESP32 Board Support 
  
  3)	Install M5Stack Library
  
  4)  ...
  
  **B. For Windows:**
  
  https://m5stack.readthedocs.io/en/latest/get-started/m5stack_core_get_started_Arduino_Windows.html
  
  or try https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-mac-and-linux-instructions/

### Step 3

Plug in your M5Stack to your computer via the provided USB cable, and switch it on if not done so via the red button on the left hand side of the M5Stack. 

### Step 4

Start Arduino (from Apps or Start Menu). Check that your computer picks up the board and you have everything installed correctly by going to

	Tools --> Board

and make sure you are able to find and select 

	M5Stack-FIRE
	
near the bottom. Then, make sure

	Tools --> Port

says

	“COM#”

The # represents your USB port number through which your Arduino IDE will communicate with the M5Stack and should be picked up automatically.

Now you are ready to compile and upload code onto your M5Stack via the Arduino GUI. 

## (2) Run your first Arduino program: Motion_Data

The following steps will show you how to program your M5Stack to display Temperature, Acceleration, Gyro and Magnetometer readings in X, Y and Z components on the M5Stack LCD screen, and monitor one of these readings over time. You will then collect this data to complete a time series analysis.

1. open  the `saccl_gyro_reader.ino` file in the `examples/motion_data` folder and  run it using Arduino.
2. Wait to see sensory values on the M5stack screen.
3. Go to `Tools > Serial Monitor or Cntrl+Shift+M`.
4. You can see the plot, shake the M5Stack to see changes in readings!

#### Useful information about this script for customisation:

The first two lines of the code are:

```
#include <M5Stack.h>  
#include "utility/MPU9250.h"
```

These load up the libraries (.h files) that you have downloaded in earlier (Step 2) and will be required for the script.

Typically, an Arduino IDE script consists of a Setup and a Loop. The Setup code is completed once, scripted under “Void Setup” and usually includes information such as variable names and pin numbers, the second half is the loop that will be repeated over and over again, usually the longer half of the code, scripted under “Void Loop”.

The full script is accessible through xxx and is also pasted at the end of this document.

```
M5.Lcd.fillScreen(BLACK);
M5.Lcd.setTextColor(GREEN , BLACK);
M5.Lcd.setTextSize(2);
```

Set your M5Stack LCD screen background colour, font colour and size, and can be changed by typing in different colours within the brackets.

```
Serial.println((int)(1000 * IMU.ax));
```

Defines your variable that you want to monitor through the Serial Monitor via the Arduino GUI (Tools > Serial Monitor or Cntrl+Shift+M). You can view a live plot of the last 500 data points of this variable through the Serial Plotter (Tools > Serial Plotter or Cntrl+Shift+L). Make sure to select the correct baud rate (i.e. 115200) from the dropdown, as defined in your code line “Serial.begin(115200);” under “void Setup”.

IMU.ax are accelerometer readings, IMU.gx are Gyroscope readings, and IMU.mx are magnetometer readings in the X direction (Left-Right). Type the one you are interested in within the second inner brackets in the Serial.println line. 
Finally, the “delay(100);” command at the end of the “void Loop” section at the bottom of the script defines the delay, in milliseconds, between each loop defined within the brackets. In this case, the delay is 100ms and the loop is taking and displaying the readings. You can change this if you want to increase or decrease the time rate of sensor readings.


## (3) Read from M5Stack into Jupyter Notebook

1. open  the `temp_humi_reader.ino` file in the `examples/weather_data` folder
2. Run the file using Arduino. Wait to see data on the M5Stack screen.
3. Run the `Jupyter Notebook`.
3. open  the `plot-temp-humi-t_data.ipynb` file in the `examples/weather_data` folder with `Jupyter Notebook`.
4. Run the codes and see how it plots the tempreature vs humidity.




* To see more examples and learn how to code in Aurduino got to `File --> Examples --> M5stack`. Edit and learn!


### Contributors 
* [Fady Abayzaid](https://www.imperial.ac.uk/design-engineering/research/human-performance-and-experience/extreme-conditions-lab-ecl/)
* [Fan Vincent Mo](https://mofanv.github.io/)
* [Hamed Haddadi](https://haddadi.github.io/)
* [Mohammad Malekzadeh](https://mmalekzadeh.github.io/)
