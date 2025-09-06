# hello pico

set up a c/c++ project for RP2040

## SDK and ARM toolchain

* [PICO SDK repo](https://github.com/raspberrypi/pico-sdk)

```
$ git clone https://github.com/raspberrypi/pico-sdk
$ cd pico-sdk
$ git submodule update --init --recursive
$ export PICO_SDK_PATH="$HOME/io/tools/pico-sdk"
```

* ARM32 toolchain

Download from [ARM GNU toolchains](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)

```
$ export PICO_TOOLCHAIN_PATH="$HOME/io/tools/gnu-arm/gcc-arm-none-eabi-14.3.rel1/bin"
```

## build and load

```
$ mkdir build && cd build
$ cmake .. && make
$ cp hello-pico.uf2 /Volumes/RPI-RP2
```

* Attention:

Before running the last command, hold the BOOTSEL button of the Raspberry Pi Pico board before connecting it to the USB port. By doing so, the pico board enters the bootloader mode.

## ws2812

* create a branch and switch to it

```
$ git checkout -b ws2812
```

There is an example playing [ws2812](https://github.com/raspberrypi/pico-examples) with PIO of RP2040.

```
$ git add .
$ git commit -m 'pico-ws2812'
$ git push origin ws2812
```

## ref

* [Developing in C on RP2040: macOS](https://wellys.com/posts/rp2040_c_macos/)

* [RP2040-CLI](https://github.com/FarmBoy522/RP2040-CLI)

* [RPi doc](https://www.raspberrypi.com/documentation/microcontrollers/c_sdk.html)

* [Deepblue](https://deepbluembedded.com/raspberry-pi-pico-w-sdk-c-programming-rp2040/)

* [RP2040-FreeRTOS](https://github.com/smittytone/RP2040-FreeRTOS)

