+++
date = "2016-12-21T00:16:43+01:00"
title = "Compiling_for_nRF51822"
draft = false
+++

I have nrf51822QFAA -> 16k ram
heap size in startup file too big https://devzone.nordicsemi.com/question/3771/ld-region-ram-overflowed-with-stack/

set heap to zero in gcc_startup_nrf51.S

safe to do if you don't use malloc (<- what's that?)

set memory sizes in linker script:
https://diyiot.wordpress.com/2015/11/01/ble-application-with-nrf51822-the-linker-script/

http://infocenter.nordicsemi.com/pdf/nRF51822_PS_v3.3.pdf

softdevice s130 specification
http://infocenter.nordicsemi.com/pdf/S130_SDS_v2.0.pdf

heap vs. stack: http://gribblelab.org/CBootcamp/7_Memory_Stack_vs_Heap.html

http://stackoverflow.com/questions/2308751/what-is-a-memory-heap

https://en.wikipedia.org/wiki/Memory_management#HEAP

# embedded c tutorials
https://mail.google.com/mail/u/0/#inbox/15920642ea03eb9a
https://blog.udemy.com/embedded-c-tutorial/
https://www.udemy.com/certificate-program-in-introduction-to-microprocessors/?tc=blog.embeddedctutorial&utm_source=blog&utm_medium=udemyads&utm_content=post135834&utm_campaign=content-marketing-blog&xref=blog
http://www.embedded.com/electrical-engineer-community/general/4402974/Free-MIT-online-C-programming-course
https://www.tutorialspoint.com/embedded_systems/index.htm
http://www.learn-c.com/

# about memory in microcontrollers
memory model: https://developer.mbed.org/handbook/Memory-Model

stack in microcontrollers http://www.avr-tutorials.com/general/avr-microcontroller-stack-operation-and-stack-pointer

stack begint op laatst beschikbare adres en loopt terug.

heap begint op eerste adres na de statische variabelen en loopt op

microcontroller introduction: http://eleceng.dit.ie/frank/msp430/microcontrollers.pdf

calculating stack size http://www.keil.com/support/docs/192.htm

http://stackoverflow.com/questions/38033130/how-to-use-the-gdb-gnu-debugger-and-openocd-for-microcontroller-debugging-fr

# get memory requirement for nRF51822 configuration
https://devzone.nordicsemi.com/question/73375/how-to-adjust-the-ram-size-in-central-and-peripheral-example/

compile met -g -g3 of -ggdb https://devzone.nordicsemi.com/question/73375/how-to-adjust-the-ram-size-in-central-and-peripheral-example/

debugging nRF51822 met openocd en gdb https://devzone.nordicsemi.com/question/46287/nrf51822-segger-j-link-base-debug-probe-openocd-gdb-fails-with-sigint-0xfffffffe/

another debugging example: https://github.com/RIOT-OS/RIOT/wiki/Board:-yunjia-nrf51822

arm-none-eabi-gdb ".out file"
target remote localhost 3333
load
monitor reset halt
break main
break sd_ble_enable
c   (keep continuing until breakpoint sd_ble_enable is met)
finish (this wil finish the function the breakpoint was set on)
print app_ram_base   <- dit is app_ram_base adres dat ingesteld moet worden
print ram_start    <- dit is het ram startadres dat nu is ingesteld

http://openocd.org/doc/html/GDB-and-OpenOCD.html


power optimization
https://devzone.nordicsemi.com/question/5186/how-to-minimize-current-consumption-for-ble-application-on-nrf51822/#reply-5187
https://devzone.nordicsemi.com/question/16937/simple-nrf51822-power-consumption-examples/

https://devzone.nordicsemi.com/tutorials/7/
