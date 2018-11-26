# ZROS
Arduino Lib to support ros on Pilo / Captor board.

This library redefine the serial interface.


## Usage
write something like this :

#if defined(BOARD_ID_Pilo)
	#include <Wire.h>
	#include <SPI.h>
	#include <variant.h>
	// define on which serial interface ROS will be map : Serial0, serial1,serialFTDI, ...
	// for PILO board can be P_COMx.serialy where x is between 0 and 5 or 0_BIS and y is 2 or ""
	#define ROS_SERIAL (P_COM3.serial2)
	// define the baud rate of ros interface.
	#define ROS_BAUDRATE 57600 
	#include "ros.h" // default value is (P_COM3.serial2) at 57600,  it refers to  https://github.com/zoubworldArduino/rosserial_arduino_lib.git
	ros::NodeHandle  nh;
#elif defined(BOARD_ID_Captor)
	#include <Wire.h>
	#include <SPI.h>
	#include <variant.h>
	
	// define on which serial interface ROS will be map : Serial0, serialFTDI, ...
	// for Captor board can be Serial0(P_COM0.serial), Serial0B(P_COM0.serial2), Serial3(P_COMB.serial), Serial1_2(P_COMA.serial),SerialFTDI(Serial3B_3)
	#define ROS_SERIAL (P_COM0.serial2)
	#define ROS_BAUDRATE 57600
#include "ros.h" // it refers to  https://github.com/zoubworldArduino/rosserial_arduino_lib.git
	ros::NodeHandle  nh;

#else // any classic arduino board with 1 serial interface.
	#include "ros.h" // it refers to https://github.com/frankjoshua/rosserial_arduino_lib.git or https://github.com/zoubworldArduino/rosserial_arduino_lib.git
	ros::NodeHandle  nh;
#endif