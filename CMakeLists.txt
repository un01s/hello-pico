cmake_minimum_required(VERSION 3.13)

# Include the Pico SDK initialization script
include($ENV{PICO_SDK_PATH}/pico_sdk_init.cmake)

project(hello-pico)

# Initialize the Pico SDK
pico_sdk_init()

# Add your executable and source files
add_executable(hello-pico
    main.cpp
)

# Enable USB stdio and disable UART stdio
pico_enable_stdio_usb(hello-pico 1)
pico_enable_stdio_uart(hello-pico 0)

# Link the Pico SDK to your project
target_link_libraries(hello-pico pico_stdlib)

# Create map/bin/hex/uf2 files
pico_add_extra_outputs(hello-pico)
