# Lab 4- Embedded Systems Development - 04633-A

The servo motor control implementation on STM32, our team adopted a comprehensive approach encapsulating both hardware and software aspects to ensure seamless operation and integration within our system. The development was structured into several key phases as described below:

### Contents

> **1. Hardware Abstraction and Initial Setup:**

> We initiated the project by configuring the underlying hardware resources essential for servo motor control. This involved setting up the appropriate GPIO (General Purpose Input Output) pins and timers to generate PWM (Pulse Width Modulation) signals. The stm32f4xx_hal_msp.c file was instrumental in this phase, where we enabled the clock for the relevant peripherals and configured the GPIOs for alternate function to output PWM signals. Specifically, we focused on TIM2 peripheral initialization, as it provides the PWM functionality needed to control the servo motor.
