# EXPERIMENT-02-INTERFACING-A-DIGITAL-INPUT-OUTPUT-TO-IOT-DEVELOPMENT-BOARD


**DATE:01-04-26**

**NAME: ANJALI K**

**ROLL NO: 212224040024**

**DEPARTMENT:CSE**

## Aim

To Interface a Digital Input (IR pair ) to ARM IOT development board and write a program to obtain the data

## Components required

- STM32 CUBE IDE
- ARM IOT development board
- STM programmer tool
- IR Pair Sensor

## Theory

The ARM (Advanced RISC Machine) architecture is widely used in microcontrollers and processors due to its efficiency, low power consumption, and high performance. ARM processors follow the Reduced Instruction Set Computing (RISC) design, making them ideal for embedded systems, mobile devices, and IoT applications. Many well-known semiconductor companies, including STMicroelectronics, use ARM-based architectures to develop powerful and energy-efficient microcontrollers.

One such microcontroller is the STM32WLE5JC, which is part of the STM32 family and is based on the ARM Cortex-M4 core. It is specifically designed for LoRaWAN® and other sub-GHz wireless communication applications, making it ideal for IoT and LPWAN (Low Power Wide Area Network) solutions. This microcontroller integrates a LoRa® transceiver, eliminating the need for an external radio module and reducing both cost and power consumption. With a maximum clock speed of 48 MHz, 256 KB of Flash memory, and 64 KB of RAM, it provides enough computing power for real-time data processing and wireless communication.

The STM32WLE5JC is known for its ultra-low power consumption, making it perfect for battery-operated IoT devices such as smart agriculture sensors, environmental monitoring systems, industrial automation, and asset tracking. It supports multiple communication interfaces, including I2C, SPI, and UART, allowing seamless integration with various sensors and peripherals. Additionally, it features built-in security capabilities such as AES 256-bit encryption and a True Random Number Generator (TRNG) for secure data transmission.

With its power-efficient design, built-in LoRaWAN support, and flexible communication options, the STM32WLE5JC is an excellent choice for developers looking to build long-range, low-power IoT applications. It is fully compatible with STM32CubeIDE and LoRaWAN middleware, making development and deployment easier for engineers and learners alike.

## IR PAIR

![image](https://github.com/user-attachments/assets/c0e0a1c8-b7be-4d10-9307-46432c31f26e)

IR technology is used in a wide range of wireless applications which includes remote controls and sensing. The infrared part in the electromagnetic spectrum can be separated into three main regions: near IR, mid-IR & far IR. The wavelengths of these three regions vary based on the application. For the near IR region, the wavelength ranges from 700 nm- 1400 nm, the wavelength of the mid-IR region ranges from 1400 nm – 3000 nm & finally for the far IR region, the wavelength ranges from 3000 nm – 1 mm.The near IR region is used on fiber optic & IR sensors, the mid-IR region is used for heat sensing and the far IR region is used in thermal imaging. The range of frequency for IR is maximum as compared to microwave and minimum than visible light.

## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   
<img width="1919" height="1079" alt="Screenshot 2026-05-01 134629" src="https://github.com/user-attachments/assets/09dcc48c-0799-4a48-bb96-291402e6fa1b" />


2. Click on FILE, click on new stm 32 project

<img width="1919" height="1079" alt="Screenshot 2026-05-01 134812" src="https://github.com/user-attachments/assets/fb17aa5e-c073-49d8-bc25-2bdce0bd9c66" />

<img width="1919" height="1079" alt="Screenshot 2026-05-01 134916" src="https://github.com/user-attachments/assets/99cf145f-7def-43c3-a16e-6ed8b9b59c91" />

3. Select the target to be programmed as shown below and click on next

![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4. Select the program name

![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)

5. Corresponding ioc file will be generated automatically

![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)


6. Select the appropriate pins as GPIO, in or out, USART or required options and configure

![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)

![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)


7. Click on Ctrl+S, automatically C program will be generated

![Screenshot 2025-03-11 134709](https://github.com/user-attachments/assets/70b83b79-1569-4f14-99d5-e2adbb4e692d)

8. Edit the program and as per required 

<img width="1919" height="1079" alt="Screenshot 2026-05-01 141550" src="https://github.com/user-attachments/assets/01d71df0-f2b6-4747-a75c-4ae77e899f26" />


9. Use project and build all 

<img width="1919" height="1079" alt="Screenshot 2026-05-01 141618" src="https://github.com/user-attachments/assets/51fda449-1211-4ccc-b1af-816230acf21f" />

10. Once the project is bulild 

<img width="598" height="388" alt="Screenshot 2026-05-01 141653" src="https://github.com/user-attachments/assets/88c43cc2-2b21-4268-80bd-463701f8b63b" />

11. connect the iot board to power supply and usb

12. After connecting open the STM cube programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)


13. Connect the STM board through the COM port, then upload the corresponding project ELF file/Hex file or Bin file in Erasing & Programming Window,while ensuring the board is in flash mode, and click on 'Start Program'.
<img width="1621" height="871" alt="image" src="https://github.com/user-attachments/assets/505822aa-ef2a-429e-962d-18444097b714" />

14.  After the file download is complete, switch your board to run mode and press the reset button to see the output


## STM 32 CUBE PROGRAM

```
#include "main.h"
#include "stdbool.h"
bool IRSENSOR;
void IRPAIR();
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
while (1)
  {
    IRPAIR();
}
void IRPAIR()
{
	IRSENSOR=HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_4);
	if(IRSENSOR==0){
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
		HAL_Delay(1000);
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		HAL_Delay(1000);
	}
	else{
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		HAL_Delay(1000);
	}
}
```

## OUTPUT

<img width="900" height="1600" alt="image" src="https://github.com/user-attachments/assets/f1539f8d-e4c5-4615-ae35-fd6435902f38" />
<img width="900" height="1600" alt="image" src="https://github.com/user-attachments/assets/481eeca4-8d8a-4032-9092-5ac46bc79cb8" />


## Result

Interfacing a digital Input (ir pair) with ARM microcontroller based IOT development is executed and the results are verified.
<img width="1919" height="1079" alt="Screenshot 2026-05-01 134629" src="https://github.com/user-attachments/assets/6b8ee87d-2c96-4e6e-99ec-afd8456591ac" />
