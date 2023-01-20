cmake_minimum_required(VERSION 3.13)
include(pico_sdk_import.cmake)
project(turnigy-9x-to-usb C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(turnigy_9x_to_usb)

#pico_generate_pio_header(motor_controller ${CMAKE_CURRENT_LIST_DIR}/pwm.pio)

target_sources(turnigy_9x_to_usb PUBLIC 
	${CMAKE_CURRENT_LIST_DIR}/main.c
	${CMAKE_CURRENT_LIST_DIR}/usb_descriptors.c
	)

target_include_directories(turnigy_9x_to_usb PUBLIC
	${CMAKE_CURRENT_LIST_DIR}
	)

target_link_libraries(turnigy_9x_to_usb PUBLIC
	pico_stdlib
	tinyusb_device
	tinyusb_board
	hardware_gpio
	#hardware_pio
	#hardware_adc
	)

pico_enable_stdio_usb(turnigy_9x_to_usb 1)
pico_add_extra_outputs(turnigy_9x_to_usb)
