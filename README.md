## TaskManagerIO scheduling and event based library for Arudino and mbed

### Library status

**This library is under heavy development and is not yet ready for anyone to use in their projects. Continue to use the task manager in IoAbstraction for the moment**. 

## Summary and what's supports:

TaskManagerIO is an evolution of the task management class that was originally situated in IoAbstraction, and now moved here. TaskManager is very popular in that framework because it makes programming complex tasks easier, and works across a wide range of devices. Now, we are in a new era of embedded development, where multiple threads (and even cores) have become a relatity. 

TaskManagerIO has been built from the ground up to handle this new reality while still working on many boards. Any sketch that worked on IoAbstraction task manager will work with this library unaffected. Further, it uses a lock free design, based on compare and exchange to acheive thread safety on larger boards,   atomic operations on AVR, and interrupt locking on other boards.

* Simple coroutines style task management, execute now, at a point in time, or on a schedule.
* Ability to add events from different threads for either delayed or immediate execution. 
* Polled event based programming where you set a schedule to be asked if you're event is ready to fire.
* Interrupt and external thread event based programming, where you create an event then trigger it from an interrupt or other thread.
* Marshalled interrupt support, where task manager handles the raw interrupt ISR, and then calls your interrupt task.

### Known working and supported boards:

| CPU / OS  | Boards using CPU  | Status    | Threading  |
| --------- | ----------------- | --------- | ---------- |
| ARM mbed  | STM32, nRF.       | Supported | CAS locking|
| ESP8266   | Node MCU, Huzzah  | Supported | Interrupt  |
| ESP32     | Wifi32, Huzzah32  | Supported | CAS locking|
| SAMD ARM  | MKR, IoT, Zero.   | Supported | Interrupt  |
| AVR       | Uno, Mega Mighty  | Supported | Interrupt  |

### Threading key:

* CAS locking: Protected against access even by multiple cores by using CAS task locking
* Interrupt: Single core device that is protected by an atomic noInterrupt block

## What is TaskManagerIO?

TaskManagerIO library is not a full RTOS, rather it can be used on top of FreeRTOS via ESP32 or mbed RTOS. It is a complimentary technology that can assist with certain types of work-load. It has a major advantage, that the same code runs on many platforms as listed above. It is a core building block of [IoAbstraction](https://github.com/davetcc/IoAbstraction)

## Helping out

At the moment the library is under heavy development. Please contact me first either using an issue here or [https://www.thecoderscorner.com/contact-us/] so that we don't duplicate effort.
 
