# ESE-5190-LAB-2A

# TALKING LEDs

## 3.2

1)Why is bit-banging impractical on your laptop, despite it having a  much faster processor than the RP2040?
-PC-class processors keep hundreds of instructions in-flight on a single core at once, which has drawbacks when trying to switch rapidly between hard real time tasks. Thus, bit - banging is impractical on a laptop despite it having much higher processor speeds.

2) What are some cases where directly using the GPIO might be a better choice than using the PIO hardware? 
-A PIO state machine gets a lot more done in one cycle than a Cortex-M0+ when it comes to I/O: for example, sampling a GPIO value, toggling a clock signal and pushing to a FIFO all in one cycle, every cycle. However , a PIO state machine is not remotely capable of running general purpose software.

3) The instruction here takes one data item from the transmit FIFO buffer, and places it in the output shift register (OSR). Data moves from the FIFO to the OSR one word (32 bits) at a time.

4) The state machine needs to be told which GPIO to output to depending on which pin group would be used ( out pin in this case) . Also , the GPIO needs to be told that the PIO is in control of it. Lastly , make sure that the PIO is driving the output enable line high.

5) The RP2040 has two PIO blocks, each of them with four state machines. Each PIO block has a 32-slot instruction memory which is visible to the four state machines in the block. We need to load our program into this instruction memory before any of our state machines can run the program. Once the program is loaded, we find a free state machine and tell it to run our program. 

6) This is done by the function * put_pixel() function*. This function takes its argument from another fucntion urgb_32() which converts the rgb values to rbg values which the PIO understands. At the lowest level , the **pio_sm_put_blocking** 

# 3.3 ANNOTAIONS FOR ws2812.C

![embedded_c1](https://user-images.githubusercontent.com/114244849/196307976-05af9e2a-d3d2-4847-a077-d6c97631ee3d.JPG)


![embedded_c2](https://user-images.githubusercontent.com/114244849/196308018-2ddacf39-faf4-4dc2-bf59-087eda721dcb.JPG)


![embedded_c3](https://user-images.githubusercontent.com/114244849/196308030-3c1b25bc-5c22-4dd1-a0da-bd543f8170bf.JPG)


![embedded_c4](https://user-images.githubusercontent.com/114244849/196308049-ac4486b3-2af8-4518-99c4-45e7b3e78523.JPG)


![embedded_c5](https://user-images.githubusercontent.com/114244849/196308069-88e2dddb-4e3c-42c7-804f-8d6d05becd84.JPG)


