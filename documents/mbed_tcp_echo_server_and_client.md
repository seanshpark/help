#### Steps to make a simple tcp echo server

1) create project
```
mkdir tcpecho
cd tcpecho
yotta init
```

2) enter project informations
```
Enter the module name: <tcpecho> tcpecho
Enter the initial version: <0.0.0> 
Is this an executable (instead of a re-usable library module)? <no> yes
Short description: Simple TCP Echo server code for study
Author:
What is the license for this project (Apache-2.0, ISC, MIT etc.)?  <Apache-2.0> 
```

3) set target
```
yotta target frdm-k64f-gcc
```

4) install modules
```
yotta install mbed-drivers
yotta install sockets
```

5) build emtpy
```
yotta build
```


6) create tcpecho.cpp

Good example:
https://github.com/ARMmbed/mbed-example-network/blob/master/test/echo-tcpserver/main.cpp

#### Internals

1) about Socket class
* https://docs.mbed.com/docs/mbed-client-guide/en/latest/api/classmbed_1_1Sockets_1_1v0_1_1Socket.html
* simple class hierarchy on top of document
 
2) Understanding TCPListener
* https://docs.mbed.com/docs/mbed-client-guide/en/latest/api/classmbed_1_1Sockets_1_1v0_1_1TCPListener.html

3) Understanding TCPStream
* https://docs.mbed.com/docs/mbed-client-guide/en/latest/api/classmbed_1_1Sockets_1_1v0_1_1TCPStream.html

4) LWIP?
* Socket is implemented with LWIP
* sal-stack-lwip/source/asynch_socket.c
```
const struct socket_api lwipv4_socket_api = {
    .stack = SOCKET_STACK_LWIP_IPV4,
    .version = SOCKET_ABSTRACTION_LAYER_VERSION,
    .init = init,
    .create = lwipv4_socket_create,
    .destroy = lwipv4_socket_destroy,
    .close = lwipv4_socket_close,
    .periodic_task = lwipv4_socket_periodic_task,
    .periodic_interval = lwipv4_socket_periodic_interval,
    .resolve = lwipv4_socket_resolve,
    .connect = lwipv4_socket_connect,
    .str2addr = str2addr,
    .bind = lwipv4_socket_bind,
    .start_listen = start_listen,
    .stop_listen = stop_listen,
    .accept = lwipv4_socket_accept,
    .reject = lwipv4_socket_reject,
    .send = lwipv4_socket_send,
    .send_to = lwipv4_socket_send_to,
    .recv = lwipv4_socket_recv,
    .recv_from = lwipv4_socket_recv_from,
    .set_option = lwipv4_socket_set_option,
    .get_option = lwipv4_socket_get_option,
    .is_connected = lwipv4_socket_is_connected,
    .is_bound = lwipv4_socket_is_bound,
    .get_local_addr = lwipv4_get_local_addr,
    .get_remote_addr = lwipv4_get_remote_addr,
    .get_local_port = lwipv4_get_local_port,
    .get_remote_port = lwipv4_get_remote_port,
};
```
* sockets/source/v0/Socket.cpp wraps to above socket functions

#### Client

1) Client example
* https://github.com/ARMmbed/mbed-example-network/tree/master/test/helloworld-tcpclient
