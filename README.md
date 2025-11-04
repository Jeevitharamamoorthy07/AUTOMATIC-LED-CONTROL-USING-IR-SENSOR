# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1920" height="1063" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/a23988d8-b4ff-4d87-9213-d8cce8765671" />

2. Click **File → New STM32 Project**.
![WhatsApp Image 2025-11-04 at 09 48 04_9806cbd4](https://github.com/user-attachments/assets/998d0be0-e654-4936-93ad-6504da4da4b9)

![WhatsApp Image 2025-11-04 at 08 33 45_51aec8eb](https://github.com/user-attachments/assets/dd5dd10e-6324-48f6-8ca5-291486d79d00)

3. Select the **target microcontroller** or board and click **Next**.
   ![WhatsApp Image 2025-11-04 at 08 35 02_7d0b64e0](https://github.com/user-attachments/assets/41fe2270-f542-4115-8a7d-f5bae036c63a)


4. Name the project.
   ![WhatsApp Image 2025-11-04 at 08 35 56_574d51e3](https://github.com/user-attachments/assets/fe07c20e-bfdf-46fb-a986-5c0c294fde8f)


5. The corresponding `.ioc` file will be generated automatically.
 ![WhatsApp Image 2025-11-04 at 09 28 21_545680e5](https://github.com/user-attachments/assets/4832eb43-3c2a-4367-8c2f-85b31f53f41d)

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   ![WhatsApp Image 2025-11-04 at 09 28 20_2120c234](https://github.com/user-attachments/assets/6480684a-e0d9-43f9-8dcf-ad1938d85493)
![WhatsApp Image 2025-11-04 at 09 28 21_9623f512](https://github.com/user-attachments/assets/1430b80f-3e16-4d6d-8b89-77983b172423)

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
 ![WhatsApp Image 2025-11-04 at 09 28 22_c175138f](https://github.com/user-attachments/assets/6c95a280-507e-423e-8196-cf08170b2bab)

8. Edit the generated main program as required.
   ![WhatsApp Image 2025-11-04 at 09 28 22_4c44bbe8](https://github.com/user-attachments/assets/bf1a63b2-8724-4794-8169-73c33dd357b5)


9. Click **Project → Build All**.
   ![WhatsApp Image 2025-11-04 at 09 29 19_1c9ad553](https://github.com/user-attachments/assets/63f0bf30-14b1-4ba9-b2d4-8a1b7ca33c86)

10. Link the **HEX file** using the post-build process.
   ![WhatsApp Image 2025-11-04 at 09 31 02_6bf84d40](https://github.com/user-attachments/assets/d0744006-aec9-4e4b-ad49-d58bc8e5249e)


11. Click **Debug** and connect the **STM Nucleo Board**.
  ![WhatsApp Image 2025-11-04 at 09 31 29_5e5534fe](https://github.com/user-attachments/assets/b48702c5-639a-4b48-87b7-3d6ed44df5c3)
![WhatsApp Image 2025-11-04 at 09 32 31_8844f56a](https://github.com/user-attachments/assets/71d468c7-ebb6-4486-ab60-830114f52ee7)


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-11-04 at 09 45 51_11d4bf90](https://github.com/user-attachments/assets/cb2cdced-85cd-42a6-9e94-c29d1318d070)


CASE 2: LED OFF
![WhatsApp Image 2025-11-04 at 09 45 52_5c38717f](https://github.com/user-attachments/assets/360cbaa1-cbb9-47a0-b4a5-0d93575dcd2a)

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




