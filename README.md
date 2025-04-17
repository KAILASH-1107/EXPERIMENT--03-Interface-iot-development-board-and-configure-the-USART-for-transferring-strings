EXPERIMENT--03-INTERFACING IOT DEVELOPMENT BOARD AND CONFIGURE USART FOR TRANSFERRING STRINGS
**DATE:07.04.2025

**NAME: V.KAILASH

**ROLL NO:212224240067

**DEPARTMENT:AIML

Aim:
To Interface iot development board for configuring the usart and transfer strings through it

Components required:
STM32 CUBE IDE, ARM IOT development board, STM programmer tool, Serial port utility tool

Theory
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

image

UART (Universal Asynchronous Receiver-Transmitter) is a serial communication protocol used to transfer data between devices. It is widely used in embedded systems, microcontrollers, and computers for short-distance communication. UART transmits and receives data asynchronously, meaning there is no shared clock signal between the sender and receiver. Instead, both devices must agree on a predefined baud rate (speed of communication).

Procedure
Click on STM 32 CUBE IDE, the following screen will appear
image

Click on FILE, click on new stm 32 project
image

image

Select the target to be programmed as shown below and click on next
Screenshot 2025-03-11 134231

Select the program name
image

Corresponding ioc file will be generated automatically
Screenshot 2025-03-11 134528

Select the appropriate pins as GPIO, in or out, USART or required options and configure
Screenshot 2025-03-11 134617 Screenshot 2025-03-11 134642

Click on Ctrl+S, automatically C program will be generated
image

Edit the program and as per required
image

Use project and build all
image

Once the project is bulild
image

Open STM32Cube Programmer
Screenshot 2025-03-11 135208

Connect the STM board through the COM port, then upload the corresponding project ELF file while ensuring the board is in flash mode, and click on 'Start Program.' After the file download is complete, switch your board to run mode and press the reset button to see the output
13.Open serial port utility

image

Check for execution of the output using run option.
STM 32 CUBE PROGRAM :
/* USER CODE BEGIN Header / /*

@file : main.c
@brief : Main program body
@attention
Copyright (c) 2025 STMicroelectronics.
All rights reserved.
This software is licensed under terms that can be found in the LICENSE file
in the root directory of this software component.
If no LICENSE file comes with this software, it is provided AS-IS.
/ / USER CODE END Header / / Includes ------------------------------------------------------------------*/ #include "main.h" #include<stdio.h>

#if defined(ICCARM) || defined(__ARMC_VERSION) #define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f) #elif defined(GNUC) #define PUTCHAR_PROTOTYPE int __io_putchar(int ch) #endif

/* Private includes ----------------------------------------------------------/ / USER CODE BEGIN Includes */

/* USER CODE END Includes */

/* Private typedef -----------------------------------------------------------/ / USER CODE BEGIN PTD */

/* USER CODE END PTD */

/* Private define ------------------------------------------------------------/ / USER CODE BEGIN PD / / USER CODE END PD */

/* Private macro -------------------------------------------------------------/ / USER CODE BEGIN PM */

/* USER CODE END PM */

/* Private variables ---------------------------------------------------------*/ UART_HandleTypeDef huart2;

/* USER CODE BEGIN PV */

/* USER CODE END PV */

/* Private function prototypes -----------------------------------------------/ void SystemClock_Config(void); static void MX_GPIO_Init(void); static void MX_USART2_UART_Init(void); / USER CODE BEGIN PFP */

/* USER CODE END PFP */

/* Private user code ---------------------------------------------------------/ / USER CODE BEGIN 0 */

/* USER CODE END 0 */

/**

@brief The application entry point.
@retval int / int main(void) { / USER CODE BEGIN 1 */
/* USER CODE END 1 */

/* MCU Configuration--------------------------------------------------------*/

/* Reset of all peripherals, Initializes the Flash interface and the Systick. */ HAL_Init();

/* USER CODE BEGIN Init */

/* USER CODE END Init */

/* Configure the system clock */ SystemClock_Config();

/* USER CODE BEGIN SysInit */

/* USER CODE END SysInit */

/* Initialize all configured peripherals / MX_GPIO_Init(); MX_USART2_UART_Init(); / USER CODE BEGIN 2 */

/* USER CODE END 2 */

/* Infinite loop / / USER CODE BEGIN WHILE */ while (1) { printf(" saveetha\n"); printf("scoft\n"); HAL_Delay(500);

  /* USER CODE END WHILE */

/* USER CODE BEGIN 3 */
} /* USER CODE END 3 */ }

PUTCHAR_PROTOTYPE { HAL_UART_Transmit(&huart2, (uint8_t*)&ch, 1, 0xFFFF); return ch; }

/**

@brief System Clock Configuration
@retval None */ void SystemClock_Config(void) { RCC_OscInitTypeDef RCC_OscInitStruct = {0}; RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
/** Configure the main internal regulator output voltage / __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2); /* Initializes the CPU, AHB and APB busses clocks / RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI; RCC_OscInitStruct.MSIState = RCC_MSI_ON; RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT; RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6; RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE; if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK) { Error_Handler(); } /* Configure the SYSCLKSource, HCLK, PCLK1 and PCLK2 clocks dividers */ RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3|RCC_CLOCKTYPE_HCLK |RCC_CLOCKTYPE_SYSCLK|RCC_CLOCKTYPE_PCLK1 |RCC_CLOCKTYPE_PCLK2; RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI; RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1; RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1; RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1; RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK) { Error_Handler(); } }

/**

@brief USART2 Initialization Function
@param None
@retval None */ static void MX_USART2_UART_Init(void) {
/* USER CODE BEGIN USART2_Init 0 */

/* USER CODE END USART2_Init 0 */

/* USER CODE BEGIN USART2_Init 1 */

/* USER CODE END USART2_Init 1 / huart2.Instance = USART2; huart2.Init.BaudRate = 9600; huart2.Init.WordLength = UART_WORDLENGTH_8B; huart2.Init.StopBits = UART_STOPBITS_1; huart2.Init.Parity = UART_PARITY_NONE; huart2.Init.Mode = UART_MODE_TX_RX; huart2.Init.HwFlowCtl = UART_HWCONTROL_NONE; huart2.Init.OverSampling = UART_OVERSAMPLING_16; huart2.Init.OneBitSampling = UART_ONE_BIT_SAMPLE_DISABLE; huart2.Init.ClockPrescaler = UART_PRESCALER_DIV1; huart2.AdvancedInit.AdvFeatureInit = UART_ADVFEATURE_NO_INIT; if (HAL_UART_Init(&huart2) != HAL_OK) { Error_Handler(); } if (HAL_UARTEx_SetTxFifoThreshold(&huart2, UART_TXFIFO_THRESHOLD_1_8) != HAL_OK) { Error_Handler(); } if (HAL_UARTEx_SetRxFifoThreshold(&huart2, UART_RXFIFO_THRESHOLD_1_8) != HAL_OK) { Error_Handler(); } if (HAL_UARTEx_DisableFifoMode(&huart2) != HAL_OK) { Error_Handler(); } / USER CODE BEGIN USART2_Init 2 */

/* USER CODE END USART2_Init 2 */

}

/**

@brief GPIO Initialization Function
@param None
@retval None */ static void MX_GPIO_Init(void) {
/* GPIO Ports Clock Enable */ __HAL_RCC_GPIOA_CLK_ENABLE();

}

/* USER CODE BEGIN 4 */

/* USER CODE END 4 */

/**

@brief This function is executed in case of error occurrence.
@retval None / void Error_Handler(void) { / USER CODE BEGIN Error_Handler_Debug / / User can add his own implementation to report the HAL error return state / __disable_irq(); while (1) { } / USER CODE END Error_Handler_Debug */ }
#ifdef USE_FULL_ASSERT /**

@brief Reports the name of the source file and the source line number
    where the assert_param error has occurred.
@param file: pointer to the source file name
@param line: assert_param error line source number
@retval None */ void assert_failed(uint8_t file, uint32_t line) { / USER CODE BEGIN 6 / / User can add his own implementation to report the file name and line number, ex: printf("Wrong parameters value: file %s on line %d\r\n", file, line) / / USER CODE END 6 / } #endif / USE_FULL_ASSERT */
Output screen shots of Serial port utility :
Screenshot (95)

Result :
The IoT development board was successfully interfaced, and the USART was configured to transmit strings. The transmitted data was verified using a serial monitor, confirming proper communicatio
