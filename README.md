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