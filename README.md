# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/fbd3be27-e6c2-4281-a5a4-0e22ea378c84" />


3. Click **File → New STM32 Project**.
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/6a819382-42c3-445d-af58-a893fa285158" />


4. Select the **target microcontroller** or board and click **Next**.
<img width="1920" height="1200" alt="Screenshot 2025-10-28 111618" src="https://github.com/user-attachments/assets/8602b781-3689-4c9d-b1df-363a34f20ec3" />

5. Name the project.
   
   <img width="473" height="539" alt="image" src="https://github.com/user-attachments/assets/fd03c3b3-a96f-4e13-917b-cf9f971ca820" />

6. The corresponding `.ioc` file will be generated automatically.
 <img width="1920" height="1200" alt="Screenshot 2025-10-28 111802" src="https://github.com/user-attachments/assets/4634ac37-2b32-4976-8f44-c66c07db86cd" />

7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1200" alt="Screenshot 2025-10-28 112032" src="https://github.com/user-attachments/assets/0c942826-8657-44d3-b1e6-376009555a05" />

8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
9. Edit the generated main program as required.
   <img width="1920" height="1200" alt="Screenshot 2025-10-28 112447" src="https://github.com/user-attachments/assets/905cd6f9-fed7-439f-82c2-f751926c945c" />

10. Click **Project → Build All**.
   <img width="1920" height="1200" alt="Screenshot 2025-10-28 112447" src="https://github.com/user-attachments/assets/692dd36b-e86e-46bf-88f9-44cc4f7ce2bc" />

   
11. Link the **HEX file** using the post-build process.
    <img width="721" height="268" alt="Screenshot 2025-10-28 112259" src="https://github.com/user-attachments/assets/fad2ee13-6776-4a2a-90f3-a494755a3713" />


12. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/edff6455-9b29-46e3-a507-68d41e150551" />

13. Click **Run** to execute the program.
    
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
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="631" height="407" alt="image" src="https://github.com/user-attachments/assets/79a974e1-6724-42fc-9bd1-7d15b40c6f11" />

CASE 2: LED OFF

<img width="632" height="401" alt="image" src="https://github.com/user-attachments/assets/4e411bea-fd8a-4af0-9702-b81709942d7e" />



---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
