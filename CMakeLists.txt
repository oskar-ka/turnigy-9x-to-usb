cmake_minimum_required(VERSION 3.12)
include(pico_sdk_import.cmake)
project(turnigy-9x-to-usb C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(turnigy_9x_to_usb)

#pico_generate_pio_header(motor_controller ${CMAKE_CURRENT_LIST_DIR}/pwm.pio)

target_sources(turnigy_9x_to_usb PRIVATE t9xtu.c)

target_link_libraries(turnigy_9x_to_usb PRIVATE
	pico_stdlib
	#hardware_pio
	hardware_gpio
	#hardware_adc
	)

pico_enable_stdio_usb(turnigy_9x_to_usb 1)
pico_add_extra_outputs(turnigy_9x_to_usb)
