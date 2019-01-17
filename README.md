# Control LED with Bluetooth commands - IOT#
You can turn off, turn on, set timer for LED to stay on and change intensity of LED through this project.

This project is written for STM32 specially STM32F030.
You can try this on other kinds of STM microcontrollers. (please inform me if there is any error on other devices.)

Watch the video of project on YouTube to know how it works. [Click here.](https://youtu.be/LamMGq5gNFQ)

I describe all parts of project with comments in the *main.c* file. The Project has 3 important parts:

1. Receive the commands with UART
2. Process the command in *HAL_UART_RxCpltCallback* function
3. Apply the result on LED

## Requirements (Hardware)
- Absolutely you need a STM32 microcontroller.
- Bluetooth module (I use HC-05 module for my own)
- LED and resistor (you can use relay if you don't like resistor circuit)
- PIR sensor (for detecting any move in the area)
- STM32 Programmer

## Requirements (Software)
- An application for Bluetooth terminal on your phone. (I recommend you "Serial Bluetooth Terminal" or "BT terminal" application because as i tested  many applications, some of them didn't work well and didn't send the command correctly.)
- STM32CubeMX
- IAR workbench (or any other IDE for coding. you can see the complete list in the STM32 website.)

## Commands
Here are all commands that you can send through Bluetooth to microcontroller:

##### !Be careful that **all commands have 3 letters**.

- **Lon**: This command turn LED on. LED won't turn on if you don't send this massage. Also LED may turn off if PIR sensor send *0*. It's important to consider that LED is on only if **LED has turned on by user** and **PIR sensor detect move in the area**. 
- **Lof** : This command means turn LED off. LED will never turn on if you send this command.
- **T##**: Set timer for LED. You can send any number from **11** to **99** instead of **##** in the command. The number that you send will **multiple to 100** ex. if you send "T50", the timer is set on 5000 ms (5 seconds). So when PIR sensor's data toggled to zero, LED will turn off after 5 seconds.
- **In#**: Set Intensity for LED. This function works with PWM. You can send any number from **0** to **9** instead of **#** in the command. **0** means the lowest intensity which is equal to *off* and **9** is the highest intensity of LED.

#### !If you see any problem, Please tell me. Thank you.

![image of stm32](https://cdn.pbrd.co/images/HWRTov9G.jpg)
 
