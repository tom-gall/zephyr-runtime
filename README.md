# Zephyr uTVM Runtime

This sample application is intended to be used with
[Zephyr RTOS](https://github.com/zephyrproject-rtos/zephyr), and generates
a uTVM Runtime binary for supported boards.

## Directory Structure

The application assumes that [TVM](https://github.com/apache/tvm) is located
one level higher than this sample application. 

You can generate an appropriate file structure via:

```bash
$ mkdir myproject && cd myproject
$ git clone https://github.com/apache/tvm.git
$ git clone https://github.com/tom-gall/zephyr-runtime.git
```

## Building

Assuming that you have Zephyr previously installed on your system
([getting started](https://docs.zephyrproject.org/latest/getting_started/index.html)),
you can build the runtime via some variation of the following:

```bash
$ source <zephyrpath>/zephyr/zephyr-env.sh
$ west build -p -b stm32f746g_disco zephyr-runtime/ --
$ west flash
```
