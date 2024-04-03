# Lab 4- Embedded Systems Development - 04633-A

The servo motor control implementation on STM32, our team adopted a comprehensive approach encapsulating both hardware and software aspects to ensure seamless operation and integration within our system. The development was structured into several key phases as described below:

### Servo Motor Implementation

> **1. Hardware Abstraction and Initial Setup:**

> We initiated the project by configuring the underlying hardware resources essential for servo motor control. This involved setting up the appropriate GPIO (General Purpose Input Output) pins and timers to generate PWM (Pulse Width Modulation) signals. The stm32f4xx_hal_msp.c file was instrumental in this phase, where we enabled the clock for the relevant peripherals and configured the GPIOs for alternate function to output PWM signals. Specifically, we focused on TIM2 peripheral initialization, as it provides the PWM functionality needed to control the servo motor.

> **2. Interrupt and Exception Handling:**

> To ensure robust operation, we paid special attention to the interrupt and exception management, which was handled in the stm32f1xx_it.c and stm32f4xx_it.c files for different STM32 series respectively. These files were tailored to manage the core system exceptions and interrupts, ensuring that our servo control logic could operate without disruptions and handle any unexpected events gracefully.

> **3. System Clock Configuration:**

> Recognizing the importance of accurate timing for PWM control, we configured the system clocks in the system_stm32f1xx.c and system_stm32f4xx.c files. This setup was crucial to ensure that the timers used for PWM generation were running at the correct frequencies, thereby providing precise control over the servo motor's position.

> **4. Integration and Testing:**

> Upon establishing a solid foundation with the hardware abstraction and system configuration, we integrated our PWM control logic with the rest of the system. This involved writing and testing the code responsible for generating PWM signals with varying duty cycles to control the angle of the servo motor.

> **5. Optimization and Refinement:**

> In the final phase, we focused on optimizing the control algorithms and refining the system to enhance performance and reliability. This involved fine-tuning the PWM parameters and implementing additional features such as angle limits and acceleration control to improve the responsiveness and safety of the servo motor operation.

### Keypad Implementation

> Our team embarked on a project to implement a keypad interface for a microcontroller-based system. This document describes the key steps and methodologies we adopted in our development process.

> Initially, we defined the hardware abstraction layer for the keypad in KeyPadConfig.h. Here, we specified the GPIO ports and pins for the keypad's columns and rows. We used GPIO ports D and G for the columns and ports G and B for the rows, adhering to our hardware design constraints. We also defined a debounce time of 20ms to ensure stable keypress detection.

> Subsequently, in KeyPad.h, we designed a KeyPad_t data structure to encapsulate the keypad's essential attributes, including column size, row size, and the last key pressed. This structure facilitated a clean and organized approach to handling keypad states.

> The core implementation was carried out in KeyPad.c, where we implemented several critical functions. The KeyPad_Init function initialized the GPIO pins for the keypad's columns as outputs and rows as inputs, setting an appropriate pull-up or pull-down resistor configuration to ensure reliable operation. We carefully initialized all column pins to a default high state and configured row pins to detect a pressed key when the state transitions to low.

> The KeyPad_Scan function was designed to efficiently scan the keypad by iterating over columns and rows, identifying any pressed key by checking the state of row pins when a particular column was driven low. We incorporated a delay of 5ms after each column activation to allow signal stabilization and an additional debounce delay upon detecting a key press to filter out spurious signals.

> For higher-level interaction, we developed KeyPad_WaitForKey and KeyPad_WaitForKeyGetChar, allowing users to block execution until a key press is detected or a specified timeout elapses. These functions are crucial for scenarios where the system needs to pause execution awaiting user input.
