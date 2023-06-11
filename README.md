# fan-control
EE30186_CourseWork

GENERAL INFORMATION

	Abstract

		This software tries to control a three-pin fan thanks to a Nucleo070RB Board with a STM32 microcontroller.

		The program is written in C++Mbed.

	Usage

		The user can access two operation modes after the introduction animation: open-loop control and closed-loop control.

	Software Description

		Overall the software has a main function for all the animation and looping around the different options the user chooses.
		
		On the LCD, the user should be able to select the desired speed and will be shown the measured speed.

SYSTEM REQUIREMENTS

	Hardware

		LCD 16x2
		3-pin FAN
		Breadboard
		Potentiometer
		Two buttons and two 10k resistances
		Nucleo Board
		Extension board
		A 12V power supply
		20s pin ribbon cable
	
	Software

		C++ Debugging Platform able to build .bin file
		Mbed Studio v6.0
		Windows OS (Version 9.0 or above)
		All the required drivers
	
	Files included in the software.

		main.cpp
		TextLCD.cpp: manage the display on the LCD
		TextLCD.h
		TachoRead.cpp: reads the speed from the tacho pin
		TachoRead.h
		QEI.cpp: reads the encoder value from the encoder pins and assigns the PWM value of the fan.
		QEI.h
		PIDControl.cpp: control the fan with PID control
		PIDControl.h
		MenuSettingOpenLoop.cpp: option menu to be displayed on the LCD
		MenuSettingOpenLoop.h
		mbed_app.json: write float numbers

SETTING UP THE HARDWARE

	Connect the extension board to the left side of the Nucleo Board

	Connect the fan

	On the breadboard:
		Connect the LCD to the required pin described in the TextLCD. (PB_5,PB_4,PC_7,PB_6,PA_7,PA_6) PinName rs, PinName e, PinName d4, PinName d5, PinName d6, PinName d7).
		Connect the potentiometer.
		Connect the two push buttons and the resistor.
		Connect the power supply to the two pins but don't turn the current.
		Connect every ribbon 5V pins.
		Make sure nothing is short-circuited.
		Set the power supply on 12V.

	Connect the Nucleo board to the USB port of your PC.

	Take the CourseWork.bin file and drag it to the file explorer icon (ie: NOD_F070RB (D:).

	You should see a little animation and a welcoming message.

USER MANUAL

	If the implementation is done on time, you could play the game and jump the obstacle with the blue push button.

	After waiting for the introduction message, it will show:
		"Selection Option": the user will have the choice between Closed Loop and Open Loop.
		To navigate between options, please use the blue button.
		Once your selection is made, please hold the blue button for half a second to confirm your choice.

	After confirming your choice, two options are offered: 
		- In the Open-Loop menu:
			We will ask the user to choose the percentage of the fan's speed that he wishes to reach.
			Rotate the encoder to reach the desired speed.
			To see the live speed of the fan (in RPM), navigate with the far right push-button on the breadboard. This will allow you to switch between the two displays. 
		
		- In the Closed-Loop menu: the closed loop is obviously tunable in the code but the Ziegler Method is very hard to implement for a 3-pin fan.
			We will ask the user to choose the fan's speed (in RPM) that he wishes to reach.
			Rotate the encoder to reach the desired speed.
			The first display of the Closed-Loop menu shows TS (target speed) and MS (Measured Speed)
			The second display shows the calculated PWM PID value between 0 and 1.
			To navigate between displays, please use the far left push button.

To come back to the control system please, reset it with the black button situated on the Nucleo Board
