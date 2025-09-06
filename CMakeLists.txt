cmake_minimum_required(VERSION 3.13)

# Include the Pico SDK initialization script
include($ENV{PICO_SDK_PATH}/pico_sdk_init.cmake)

project(pico-ws2812)

# Initialize the Pico SDK
pico_sdk_init()

# Add your executable and source files
# use main.cpp for hello-pico
#add_executable(pico-ws2812
#    main.cpp
#)

# Enable USB stdio and disable UART stdio
#pico_enable_stdio_usb(pico-ws2812 1)
#pico_enable_stdio_uart(pico-ws2812 0)

# pico-ws2812
add_executable(pico-ws2812)

file(MAKE_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/generated)

# generate the header file into the source tree as it is included in the RP2040 datasheet
pico_generate_pio_header(pico-ws2812 ${CMAKE_CURRENT_LIST_DIR}/ws2812.pio OUTPUT_DIR ${CMAKE_CURRENT_LIST_DIR}/generated)

target_sources(pico-ws2812 PRIVATE ws2812.c)

# Link the Pico SDK to your project
target_link_libraries(pico-ws2812 pico_stdlib hardware_pio)

pico_add_extra_outputs(pico-ws2812)

# Additionally generate python and hex pioasm outputs for inclusion in the RP2040 datasheet
add_custom_target(pio_ws2812_datasheet DEPENDS ${CMAKE_CURRENT_LIST_DIR}/generated/ws2812.py)
add_custom_command(OUTPUT ${CMAKE_CURRENT_LIST_DIR}/generated/ws2812.py
        DEPENDS ${CMAKE_CURRENT_LIST_DIR}/ws2812.pio
        COMMAND pioasm -o python ${CMAKE_CURRENT_LIST_DIR}/ws2812.pio ${CMAKE_CURRENT_LIST_DIR}/generated/ws2812.py
        VERBATIM)
add_dependencies(pico-ws2812 pio_ws2812_datasheet)

# Create map/bin/hex/uf2 files
pico_add_extra_outputs(pico-ws2812)
