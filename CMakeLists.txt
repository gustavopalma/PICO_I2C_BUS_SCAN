cmake_minimum_required(VERSION 3.12)

include(pico_sdk_import.cmake)

project(i2c_bus_scan C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

#Caso seja a Raspberry Pi Pico W
set(PICO_BOARD pico_w)
#Caso seja a Raspberry Pi Pico 
#set(PICO_BOARD pico)

pico_sdk_init()

add_executable(i2c_bus_scan bus_scan.c)

#Caso seja a Raspberry Pi Pico 
#target_link_libraries(int pico_stdlib)

#Caso seja a Raspberry Pi Pico W
target_link_libraries(i2c_bus_scan pico_cyw43_arch_none pico_stdlib hardware_i2c)

pico_enable_stdio_usb(i2c_bus_scan 1)
pico_enable_stdio_uart(i2c_bus_scan 0)

pico_add_extra_outputs(i2c_bus_scan)