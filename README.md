
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
 <img width="1920" height="1200" alt="Screenshot (214)" src="https://github.com/user-attachments/assets/a4496d72-2bab-4a5f-8c1e-d17f32b937ce" />


2. Click **File → New STM32 Project**.
  <img width="1920" height="1200" alt="Screenshot (215)" src="https://github.com/user-attachments/assets/08169e37-7112-40f2-819c-3bfc9df75237" />


3. Select the **target microcontroller** or board and click **Next**.
   <img width="1920" height="1200" alt="Screenshot (217)" src="https://github.com/user-attachments/assets/09cce37b-8931-4a87-995d-b4fd82389dcd" />


4. Name the project.
   <img width="590" height="634" alt="Screenshot (218)" src="https://github.com/user-attachments/assets/6e6f9115-501f-402e-badc-4ef1f8a14dcf" />


5. The corresponding `.ioc` file will be generated automatically.
   ![WhatsApp Image 2025-10-29 at 08 40 47_7634af0a](https://github.com/user-attachments/assets/90f1f5c7-6250-4e56-8f9c-890ecbb67de1)


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1200" alt="Screenshot (219)" src="https://github.com/user-attachments/assets/04a853ed-4d2c-4429-91f0-11f6d8e56dfb" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1920" height="1200" alt="Screenshot (220)" src="https://github.com/user-attachments/assets/855999cb-4908-4152-bf60-0e914f0c9fd9" />

 
8. Edit the generated main program as required.
   <img width="1920" height="1200" alt="Screenshot (222)" src="https://github.com/user-attachments/assets/85871e1d-d0b6-452f-8599-dd6793e6d0ff" />


9. Click **Project → Build All**.
    ![WhatsApp Image 2025-10-29 at 09 04 58_6ab2b352](https://github.com/user-attachments/assets/ecaff044-c944-42c8-ba18-a8e3709c9f7e)


10. Link the **HEX file** using the post-build process.
    <img width="1003" height="518" alt="Screenshot (221)" src="https://github.com/user-attachments/assets/aa39a5b0-9616-4de0-aee3-b98df8e31822" />

>

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="870" height="764" alt="image" src="https://github.com/user-attachments/assets/67198bec-5d09-4dd8-bfa9-b3719417d870" />

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

<img width="1280" height="576" alt="image" src="https://github.com/user-attachments/assets/5837757b-332b-487a-8820-10c96b5f31f0" />

CASE 2: LED OFF

<img width="1280" height="576" alt="image" src="https://github.com/user-attachments/assets/b9f673ed-de98-4519-bfea-a9081039cf79" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
