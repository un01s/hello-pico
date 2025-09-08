# notes on RP2040

## PIO (programmable I/O co-processor) on RP2040 for ws2812 LED

two PIO blocks. each has four state-machines with FIFO to GPIOs. the PIO has its own interrupts and can be used with DMA.

| instructions | notes |
| ------------ | ----- |
| in() | shift bits into the input shift register (ISR) |
| out() | shift bits out of the output shift register (OSR) |
| push() | push content of ISR into RX FIFO |
| pull() | load a 32bit word from the TX FIFO into the OSR |
| mov() | Copy data from source to destination |
| irq() | set or clear interrupt flags |
| wait() | wait until condition is met |
| jmp() | Jump to a label |
| set() | write immediate value to destination |

there is a PIO assembler to support the above instructions and more like ```nop``` and special directive like ```.wrap``` with labels.

for cmake to build, call ```pico_generate_pio_header``` as follows.

```
# generate PIO header "ws2812.pio.h" inside the src directory
pico_generate_pio_header(${PROJECT_NAME} ${CMAKE_CURRENT_LIST_DIR}/ws2812.pio)
```

Each LED has a 32-bit value in GGRRBBWW for RGBW-type or GGRRBB00 for RGB-type LED such as WS2812.


