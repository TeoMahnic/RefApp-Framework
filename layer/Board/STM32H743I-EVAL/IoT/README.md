Board: STMicroelectronics [STM32H743I-EVAL](https://www.st.com/en/evaluation-tools/stm32h743i-eval.html)
------------------------------------------

Device: **STM32H743XIH6**
System Core Clock: **400 MHz**

This setup is configured using **STM32CubeMX**, an interactive tool provided by STMicroelectronics for device configuration.
Refer to ["Create Projects with STM32Cube HAL and STM32CubeMX"](https://www.keil.com/pack/doc/STM32Cube/html/index.html) for additional information.

For **STM32CubeMX** configuration settings please refer to [STM32CubeMX Configuration](STM32CubeMX/STM32CubeMX.pdf).

The Heap/stack settings and CMSIS-Driver assignments are configured in the configuration files of respective software components.

The example project can be re-configured to work on custom hardware.
Refer to ["Migrate STM32 Based Example Projects to Custom Hardware"](https://github.com/MDK-Packs/Documentation/tree/master/Porting_to_Custom_Hardware) for additional information.

### System Configuration

| System resource         | Setting
|:------------------------|:--------------------------------------------
| Heap                    | 1 kB (configured in the STM32CubeMX)
| Stack (MSP)             | 1 kB (configured in the STM32CubeMX)

### STM32CubeMX configuration
Changes made starting from default STM32H743I-EVAL board setup.
1. Under **Pinout & Configuration** select **Categories - System Core - SYS**:
    - Select **TIM17** for **Timebase Source**
1. Under **Pinout & Configuration** select **Categories - System Core - NVIC**:
    - Under **NVIC** tab change:
      - **USART1 global interrupt - Enabled** to **checked**
      - **SDMMC1 global interrupt - Enabled** to **checked**
      - **Ethernet global interrupt - Enabled** to **checked**
      - **USB On The Go FS global interrupt -Enabled** to **checked**
    - Under **Code Generation** tab change:
      - **System service call via SWI instruction - Generate IRQ handler** to **unchecked**
      - **Pendable request for system service - Generate IRQ handler** to **unchecked**
      - **Time base: System tick timer - Generate IRQ handler** to **unchecked**
1. Under **Project Manager** select **Project**:
    - Under **Linker Settings** change:
      - **Minimum Heap Size** set **0x400**
      - **Minimum Stack Size** set **0x400**
1. Under **Project Manager** select **Advanced Settings**:
    - Under **Generated Function Calls** section change:
      - **Do Not Generate Function Calls** to **checked** for **Peripheral Instance Name - SDMMC1** 
1. Click on **GENERATE**

## Board configuration
**Board setup**
  - Insure that the **JP10** is in the **PSU** position and connect 5V power supply to the **CN10** connector
  - Check that the Boot selection switch **SW1** is in the **0** / default position
  - Connect a **USB micro-B cable** between the **STLK** connector and your **Personal Computer**
