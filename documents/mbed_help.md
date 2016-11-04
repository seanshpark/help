##### Compiler

arm-none-eabi, version 4.8.4 from https://launchpad.net/gcc-arm-embedded/+download

##### Where to begin

* http://yottadocs.mbed.com/#installing
* https://docs.mbed.com/docs/getting-started-mbed-os/en/latest/Full_Guide/app_on_yotta/


##### Some problem and solving while playing with Yotta 

* [Yotta setting inside firewall](https://github.com/seanshpark/help/wiki/mbed-setting-yotta)

##### Prepare mbed lib/exe from empty folder

* initialize
```
cd (to somewhere)
yotta init
(follow the questions...)
```
* set target
```
yotta target frdm-k64f-gcc
```
* install mbed-drivers
```
yotta install mbed-drivers
```
* add some files in `source` folder
* add your compile options to (whatever filename).cmake file
* build
```
yotta build
```
* copy binary to target board
```
cp build/frdm-k64f-gcc/source/(your executable filename).bin /(mount path)/MBED/.
```
* press `RESET` button on the target board to reset

##### building jerryscript on mbed

this is for latest steps for `samsung/jerryscript` `embedding-dev` branch

* prepare mbed and yotta
* get embedding-dev branch
* build...
```
cd jerryscript
git checkout embedding-dev
make -f ./embedding/mbedk64f/Makefile.mbedk64f clean
make -f ./embedding/mbedk64f/Makefile.mbedk64f
make -f ./embedding/mbedk64f/Makefile.mbedk64f yotta
```

* flash
```
cp build/frdm-k64f-gcc/source/mbedk64f.bin /media/(...)/MBED/.
```

* connect serial terminal and press RESET


##### Adding network

add `socket` module

```
cd jerryscript/embedding/mbedk64f
yotta install sockets

cd ../..
make -f ./embedding/mbedk64f/Makefile.mbedk64f yotta

```


##### Debug

In your project directory
```
$ yt debug (executable filename)
```



***


With FRDM-K64F board, Ethernet is available.

#### Enable socket 

You need `socket` module install
```
yotta install sockets
```

#### Interfaces


##### EthernetInterface

https://developer.mbed.org/handbook/Ethernet-Interface

* Init ethernet with DHCP or Static IP, Netmask an Gateway.

##### TCPStream

* use sockets/TCPStream.h
```
class TCPStream: public TCPAsynch
```

* stack type
```
typedef enum {
    SOCKET_STACK_UNINIT = 0,
    SOCKET_STACK_LWIP_IPV4,
    SOCKET_STACK_LWIP_IPV6,
    SOCKET_STACK_RESERVED,
    SOCKET_STACK_NANOSTACK_IPV6,
    SOCKET_STACK_PICOTCP,
    SOCKET_STACK_MAX,
} socket_stack_t;
```

* TCPAsynch is derived from Socket
```
class TCPAsynch: public Socket 
```

##### Socket

`namespace` is `mbed::Sockets::current` for current and implementation(?) is `mbed::Sockets::v0`



***

#### ticker
Hardware timer handler

#### ticker_event_queue_t
queue of events with event handler.
```
/** Ticker's event queue structure
 */
typedef struct {
    ticker_event_handler event_handler; /**< Event handler */
    ticker_event_t *head;               /**< A pointer to head */
} ticker_event_queue_t;
```

#### initialization

in yotta_modules/mbed-hal-ksdk-mcu/source/us_ticker.c

```
void us_ticker_init(void) {
    if (us_ticker_inited) {
        return;
    }
    us_ticker_inited = 1;

    //Common for ticker/timer
    uint32_t busClock;
    CLOCK_SYS_EnablePitClock(0);
    PIT_HAL_Enable(PIT_BASE);
    CLOCK_SYS_GetFreq(kBusClock, &busClock);

    //Timer
    PIT_HAL_SetTimerPeriodByCount(PIT_BASE, 0, busClock / 1000000 - 1);
    PIT_HAL_SetTimerPeriodByCount(PIT_BASE, 1, 0xFFFFFFFF);
    PIT_HAL_SetTimerChainCmd(PIT_BASE, 1, true);
    PIT_HAL_StartTimer(PIT_BASE, 0);
    PIT_HAL_StartTimer(PIT_BASE, 1);

    //Ticker
    PIT_HAL_SetTimerPeriodByCount(PIT_BASE, 2, busClock / 1000000 - 1);
    PIT_HAL_SetTimerChainCmd(PIT_BASE, 3, true);
    vIRQ_SetVector(PIT3_IRQn, (uint32_t)us_ticker_irq_handler);
    vIRQ_EnableIRQ(PIT3_IRQn);
}
```


***


Start...

```
extern "C" int main(void) {
    minar::Scheduler::postCallback(
        FunctionPointer2<void, int, char**>(&app_start).bind(0, NULL)
    );
    // The 'start' function below doesn't actually return, since it runs
    // the MINAR's infinite event scheduler loop
    return minar::Scheduler::start();
}
```

start() is
```
int minar::Scheduler::start(){
    instance();
    return staticScheduler->data->start();
}
```

where `minar::SchedulerData::start()` loops until `stop_dispatch` is made true in `minar::Scheduler::stop()`


***

#### mbed gdb server

https://github.com/mbedmicro/pyOCD

```
pip install --pre -U pyocd
```

and start server with
```
pyocd-gdbserver
```
