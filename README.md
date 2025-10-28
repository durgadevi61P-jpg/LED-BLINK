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
   <img width="1920" height="1200" alt="Screenshot (221)" src="https://github.com/user-attachments/assets/1a8747d7-8177-4dd5-a4ef-942a280c5038" />

2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-28 at 22 14 26_c495cf91](https://github.com/user-attachments/assets/53df7fe5-c0e8-4c1b-9006-cb3379db17de)


3. Select the **target microcontroller** or board and click **Next**.
   ![WhatsApp Image 2025-10-28 at 22 20 31_935bc879](https://github.com/user-attachments/assets/c4f39e43-dd24-465b-a390-60acd04380a3)


4. Name the project.
   ![WhatsApp Image 2025-10-28 at 22 21 51_54b4ddfc](https://github.com/user-attachments/assets/42e3a934-7761-422c-bbcf-f6127b571311)


5. The corresponding `.ioc` file will be generated automatically.
  ![WhatsApp Image 2025-10-28 at 22 22 54_82f1532d](https://github.com/user-attachments/assets/a09d7ef3-3fbb-4e16-a585-ae657f9a3ef5)

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   ![WhatsApp Image 2025-10-28 at 22 25 34_6c47e226](https://github.com/user-attachments/assets/50801087-e8f3-45d0-84ce-5d4786172ecf)
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
8. Edit the generated main program as required.
   ![WhatsApp Image 2025-10-28 at 22 32 46_92963b7b](https://github.com/user-attachments/assets/2e4efd40-7906-4064-96af-bf5e8bbbdc70)

9. Click **Project → Build All**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/264cd0a8-3e96-4668-822e-838ecfafc527" />

10. Link the **HEX file** using the post-build process.

     ![WhatsApp Image 2025-10-28 at 23 25 15_c5f9aa6e](https://github.com/user-attachments/assets/fb6940e1-9104-48fd-bb98-aac2782f8b6b)


11. Click **Debug** and connect the **STM Nucleo Board**.
    ![WhatsApp Image 2025-10-28 at 22 32 48_64e735cd](https://github.com/user-attachments/assets/77675f9a-5cf4-4425-9efe-2c4680042d45)

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
![WhatsApp Image 2025-10-28 at 21 58 09_ca31c82e](https://github.com/user-attachments/assets/7e4b176d-cb64-49b2-b4b0-eb4cea7e1d6d)

CASE 2: LED OFF
![WhatsApp Image 2025-10-28 at 21 53 44_96eef121](https://github.com/user-attachments/assets/50950922-0ab6-45ff-81c4-187de2018834)

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
