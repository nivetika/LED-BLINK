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
    <img width="1920" height="1200" alt="Screenshot (39)" src="https://github.com/user-attachments/assets/6c783da5-5b30-47ae-ba37-9a13755c908d" />


2. Click **File → New STM32 Project**.

   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e941a8f9-db73-4202-81d8-2f8691757370" />

   <img width="1920" height="1200" alt="Screenshot (41)" src="https://github.com/user-attachments/assets/5b72abfe-fc21-4aa7-b717-5177312574f0" />


4. Select the **target microcontroller** or board and click **Next**.

   <img width="1920" height="1200" alt="Screenshot (42)" src="https://github.com/user-attachments/assets/ab6afe9b-c25c-4dc9-a840-a181197584e8" />

6. Name the project.

   <img width="1920" height="1200" alt="Screenshot (43)" src="https://github.com/user-attachments/assets/723b7ed1-9d6d-4653-a271-744ad5440925" />


8. The corresponding `.ioc` file will be generated automatically.

   <img width="1920" height="1200" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/12ca6c23-6e6d-473f-82fc-47e32548e611" />


10. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.

    <img width="1920" height="1200" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/ee86c624-608e-4c44-a3dc-09759fc0e2e9" />
    <img width="1920" height="1200" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/72ef6c72-72e9-4a84-bf0f-15b64304489e" />


11. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.

   <<img width="1920" height="1200" alt="Screenshot (47)" src="https://github.com/user-attachments/assets/ee726be1-fb2c-4edf-9ac6-6133432c71ed" />

 
13. Edit the generated main program as required.

<<img width="1920" height="1200" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/fb36fe89-424a-4215-aa0e-04b5ebd965a8" />

15. Click **Project → Build All**.

    <img width="1127" height="530" alt="Screenshot 2025-10-28 162605" src="https://github.com/user-attachments/assets/bdf7b029-857e-4bc0-ab3f-f2598e38a6a5" />

17. Link the **HEX file** using the post-build process.

<img width="1127" height="530" alt="Screenshot 2025-10-28 162605" src="https://github.com/user-attachments/assets/34850629-e940-4b47-82b7-322c41c03088" />

19. Click **Debug** and connect the **STM Nucleo Board**.

    <img width="1920" height="1200" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/0788b0d9-cb40-49b8-ab62-d2df38187de4" />

21. Click **Run** to execute the program.
    
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

<img width="524" height="468" alt="Screenshot 2025-10-27 133521" src="https://github.com/user-attachments/assets/192488a3-fe15-4329-9a2c-8dcdce6427ab" />

CASE 2: LED OFF

![WhatsApp Image 2025-10-27 at 13 24 57_916b1201](https://github.com/user-attachments/assets/addf8d31-8ddf-4831-9b2f-e3631f74630b)

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
