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

## build

```
$ mkdir build && cd build
$ cmake .. && make
$ cp hello-pico.uf2 /Volumes/RPI-RP2
```

## ref

* [Developing in C on RP2040: macOS](https://wellys.com/posts/rp2040_c_macos/)

