#
# file: CMakeLists.txt
#
# This is the main CMakeLists.txt for STM32F0xx_HAL_Driver integration with distortos
#
# author: Copyright (C) 2020-2021 Kamil Szczygiel https://distortec.com https://freddiechopin.info
#
# This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. If a copy of the MPL was not
# distributed with this file, You can obtain one at https://mozilla.org/MPL/2.0/.
#

cmake_minimum_required(VERSION 3.8)
project(STM32F0xx_HAL_Driver-integration)

if(NOT DEFINED STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY)
	message(SEND_ERROR "Variable with path to STM32F0xx_HAL_Driver-configuration.h - "
			"STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY - is not defined")
endif()
if(NOT IS_DIRECTORY "${STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY}")
	message(SEND_ERROR "Path to STM32F0xx_HAL_Driver-configuration.h - "
			"STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY = ${STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY} - is "
			"not valid")
endif()
if(NOT EXISTS "${STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY}/STM32F0xx_HAL_Driver-configuration.h")
	message(SEND_ERROR "Path to STM32F0xx_HAL_Driver-configuration.h - "
			"STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY = ${STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY} - does "
			"not contain STM32F0xx_HAL_Driver-configuration.h")
endif()

if(NOT DEFINED STM32F0XX_HAL_DRIVER_DIRECTORY)
	message(SEND_ERROR "Variable with path to STM32F0xx_HAL_Driver directory - STM32F0XX_HAL_DRIVER_DIRECTORY - is not "
			"defined")
endif()
if(NOT IS_DIRECTORY "${STM32F0XX_HAL_DRIVER_DIRECTORY}")
	message(SEND_ERROR "Path to STM32F0xx_HAL_Driver directory - "
			"STM32F0XX_HAL_DRIVER_DIRECTORY = ${STM32F0XX_HAL_DRIVER_DIRECTORY} - is not valid")
endif()
if(NOT EXISTS "${STM32F0XX_HAL_DRIVER_DIRECTORY}/Inc/stm32f0xx_hal.h")
	message(SEND_ERROR "Path to STM32F0xx_HAL_Driver directory - "
			"STM32F0XX_HAL_DRIVER_DIRECTORY = ${STM32F0XX_HAL_DRIVER_DIRECTORY} - does not contain Inc/stm32f0xx_hal.h")
endif()

if(STM32F0xx_HAL_Driver_ADC)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's ADC")
endif()

if(STM32F0xx_HAL_Driver_DAC)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's DAC")
endif()

if(STM32F0xx_HAL_Driver_I2C)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's I2C")
endif()

if(STM32F0xx_HAL_Driver_I2S)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's I2S")
endif()

if(STM32F0xx_HAL_Driver_IRDA)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's IRDA")
endif()

if(STM32F0xx_HAL_Driver_SMARTCARD)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's SMARTCARD")
endif()

if(STM32F0xx_HAL_Driver_SPI)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's SPI")
endif()

if(STM32F0xx_HAL_Driver_TIM)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's TIM")
endif()

if(STM32F0xx_HAL_Driver_UART)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's UART")
endif()

if(STM32F0xx_HAL_Driver_USART)
	list(APPEND STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS "STM32F0xx_HAL_Driver's USART")
endif()

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_ADC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's ADC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_CAN
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's CAN module."
		NO_OUTPUT)

if(STM32F0xx_HAL_Driver_CAN)

	distortosSetConfiguration(BOOLEAN
			STM32F0xx_HAL_Driver_CAN_legacy_variant
			OFF
			HELP "Select legacy variant of STM32F0xx_HAL_Driver's CAN module."
			NO_OUTPUT)

endif(STM32F0xx_HAL_Driver_CAN)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_CEC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's CEC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_COMP
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's COMP module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_CRC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's CRC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_DAC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's DAC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_DMA
		OFF
		DEPENDENTS ${STM32F0XX_HAL_DRIVER_DMA_DEPENDENTS}
		HELP "Enable STM32F0xx_HAL_Driver's DMA module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_EXTI
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's EXTI module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_I2C
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's I2C module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_I2S
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's I2S module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_IRDA
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's IRDA module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_IWDG
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's IWDG module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_PCD
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's PCD module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_PWR
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's PWR module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_RTC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's RTC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_SMARTCARD
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's SMARTCARD module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_SMBUS
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's SMBUS module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_SPI
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's SPI module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_TIM
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's TIM module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_TSC
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's TSC module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_UART
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's UART module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_USART
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's USART module."
		NO_OUTPUT)

distortosSetConfiguration(BOOLEAN
		STM32F0xx_HAL_Driver_WWDG
		OFF
		HELP "Enable STM32F0xx_HAL_Driver's WWDG module."
		NO_OUTPUT)

message(STATUS "Generating ${CMAKE_CURRENT_BINARY_DIR}/include/stm32f0xx_hal_conf.h")
string(TIMESTAMP timestamp "%Y-%m-%d %H:%M:%S")
configure_file(stm32f0xx_hal_conf.h.in
		${CMAKE_CURRENT_BINARY_DIR}/include/stm32f0xx_hal_conf.h)

add_library(STM32F0xx_HAL_Driver STATIC
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_cortex.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_flash.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_flash_ex.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_gpio.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_rcc.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_rcc_ex.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_adc.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_comp.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_crc.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_crs.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_dac.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_dma.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_exti.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_gpio.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_i2c.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_pwr.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_rcc.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_rtc.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_spi.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_tim.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_usart.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_usb.c
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_ll_utils.c)
target_compile_options(STM32F0xx_HAL_Driver PRIVATE
		-Wno-overflow
		-Wno-unused-parameter)
target_include_directories(STM32F0xx_HAL_Driver BEFORE PUBLIC
		include)
target_include_directories(STM32F0xx_HAL_Driver PUBLIC
		${CMAKE_CURRENT_BINARY_DIR}/include
		${STM32F0XX_HAL_DRIVER_CONFIGURATION_H_DIRECTORY}
		${STM32F0XX_HAL_DRIVER_DIRECTORY}/Inc)
target_link_libraries(STM32F0xx_HAL_Driver PUBLIC
		distortos::distortos)

if(STM32F0xx_HAL_Driver_ADC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_adc.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_adc_ex.c)
endif(STM32F0xx_HAL_Driver_ADC)

if(STM32F0xx_HAL_Driver_CAN)
	if(NOT STM32F0xx_HAL_Driver_CAN_legacy_variant)
		target_sources(STM32F0xx_HAL_Driver PRIVATE
				${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_can.c)
	else()
		target_include_directories(STM32F0xx_HAL_Driver PUBLIC
				${STM32F0XX_HAL_DRIVER_DIRECTORY}/Inc/Legacy)
		target_sources(STM32F0xx_HAL_Driver PRIVATE
				${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/Legacy/stm32f0xx_hal_can.c)
	endif()
endif(STM32F0xx_HAL_Driver_CAN)

if(STM32F0xx_HAL_Driver_CEC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_cec.c)
endif(STM32F0xx_HAL_Driver_CEC)

if(STM32F0xx_HAL_Driver_COMP)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_comp.c)
endif(STM32F0xx_HAL_Driver_COMP)

if(STM32F0xx_HAL_Driver_CRC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_crc.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_crc_ex.c)
endif(STM32F0xx_HAL_Driver_CRC)

if(STM32F0xx_HAL_Driver_DAC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_dac.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_dac_ex.c)
endif(STM32F0xx_HAL_Driver_DAC)

if(STM32F0xx_HAL_Driver_DMA)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_dma.c)
endif(STM32F0xx_HAL_Driver_DMA)

if(STM32F0xx_HAL_Driver_EXTI)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_exti.c)
endif(STM32F0xx_HAL_Driver_EXTI)

if(STM32F0xx_HAL_Driver_I2C)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_i2c.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_i2c_ex.c)
endif(STM32F0xx_HAL_Driver_I2C)

if(STM32F0xx_HAL_Driver_I2S)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_i2s.c)
endif(STM32F0xx_HAL_Driver_I2S)

if(STM32F0xx_HAL_Driver_IRDA)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_irda.c)
endif(STM32F0xx_HAL_Driver_IRDA)

if(STM32F0xx_HAL_Driver_IWDG)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_iwdg.c)
endif(STM32F0xx_HAL_Driver_IWDG)

if(STM32F0xx_HAL_Driver_PCD)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_pcd.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_pcd_ex.c)
endif(STM32F0xx_HAL_Driver_PCD)

if(STM32F0xx_HAL_Driver_PWR)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_pwr.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_pwr_ex.c)
endif(STM32F0xx_HAL_Driver_PWR)

if(STM32F0xx_HAL_Driver_RTC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_rtc.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_rtc_ex.c)
endif(STM32F0xx_HAL_Driver_RTC)

if(STM32F0xx_HAL_Driver_SMARTCARD)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_smartcard.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_smartcard_ex.c)
endif(STM32F0xx_HAL_Driver_SMARTCARD)

if(STM32F0xx_HAL_Driver_SMBUS)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_smbus.c)
endif(STM32F0xx_HAL_Driver_SMBUS)

if(STM32F0xx_HAL_Driver_SPI)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_spi.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_spi_ex.c)
endif(STM32F0xx_HAL_Driver_SPI)

if(STM32F0xx_HAL_Driver_TIM)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_tim.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_tim_ex.c)
endif(STM32F0xx_HAL_Driver_TIM)

if(STM32F0xx_HAL_Driver_TSC)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_tsc.c)
endif(STM32F0xx_HAL_Driver_TSC)

if(STM32F0xx_HAL_Driver_UART)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_uart.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_uart_ex.c)
endif(STM32F0xx_HAL_Driver_UART)

if(STM32F0xx_HAL_Driver_USART)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_usart.c
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_usart_ex.c)
endif(STM32F0xx_HAL_Driver_USART)

if(STM32F0xx_HAL_Driver_WWDG)
	target_sources(STM32F0xx_HAL_Driver PRIVATE
			${STM32F0XX_HAL_DRIVER_DIRECTORY}/Src/stm32f0xx_hal_wwdg.c)
endif(STM32F0xx_HAL_Driver_WWDG)

add_library(STM32F0xx_HAL_Driver-object-library OBJECT
		APBPrescTable.cpp
		HAL_Delay.cpp
		HAL_GetTick.cpp
		SystemCoreClock.cpp)
target_include_directories(STM32F0xx_HAL_Driver-object-library PRIVATE
		$<TARGET_PROPERTY:STM32F0xx_HAL_Driver,INTERFACE_INCLUDE_DIRECTORIES>)

target_sources(STM32F0xx_HAL_Driver INTERFACE
		$<TARGET_OBJECTS:STM32F0xx_HAL_Driver-object-library>)
