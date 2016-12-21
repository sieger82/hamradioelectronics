+++
date = "2016-12-21T00:16:43+01:00"
title = "Compiling_for_nRF51822"
draft = true
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
