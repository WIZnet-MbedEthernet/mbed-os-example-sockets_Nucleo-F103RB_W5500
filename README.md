## Getting started with the network-socket API<br>Nucleo-F103RB With W5500 in Mbed Studio

### 1. Mbed Studio New Program  
- Generate Program
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set001.png" />
</p>
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set011.png" />
</p>

### 2. Build Program
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set002.png" />
</p>

### 3. Add Library
#### 1) Git-Hub Download
 - Add easy_connect Library
   [easy_connect](https://github.com/WIZnet-MbedEthernet/easy-connect.git)<br>
   git clone or Download Zip
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set003.png" />
</p>

 - Wiznet-eth-driver
   [Wiznet-eth-driver](https://github.com/WIZnet-MbedEthernet/wiznet-eth-driver.git)<br>
   git clone or Download Zip
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set004.png" />
</p>
 - Add Liberary in Active Program  
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set005.png" />
</p>

#### 2) Mbed Commend
 - Copy file easy-connect.lib [mbed-os-example-sockets_Nucleo-F103RB_W5500](https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500.git) 
 - Add easy_connect Library<br>
   Commend : mbed deploy https://github.com/WIZnet-MbedEthernet/easy-connect.git
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set006.png" />
</p>

 - Wiznet-eth-driver<br>
   Commend : mbed deploy https://github.com/WIZnet-MbedEthernet/wiznet-eth-driver.git
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set007.png" />
</p>

### 4. modify mbed_app.json file
```
{
    "config": {
        "network-interface":{
            "help": "options are ETHERNET, ETHERNET_W5500, WIFI_ESP8266, WIFI_ODIN, MESH_LOWPAN_ND, MESH_THREAD",
            "value": "ETHERNET_W5500"
        },
        "mesh_radio_type": {
            "help": "options are ATMEL, MCR20, SPIRIT1, EFR32",
            "value": "ATMEL"
        },
        "esp8266-tx": {
            "help": "Pin used as TX (connects to ESP8266 RX)",
            "value": "D1"
        },
        "esp8266-rx": {
            "help": "Pin used as RX (connects to ESP8266 TX)",
            "value": "D0"
        },
        "esp8266-debug": {
            "value": true
        },
        "wifi-ssid": {
            "value": "\"SSID\""
        },
        "wifi-password": {
            "value": "\"Password\""
        }
    },
    "target_overrides": {
        "*": {
            "target.features_add": ["NANOSTACK", "LOWPAN_ROUTER", "COMMON_PAL"],
            "platform.stdio-baud-rate": 115200,
            "platform.stdio-convert-newlines": true,
            "mbed-mesh-api.6lowpan-nd-channel-page": 0,
            "mbed-mesh-api.6lowpan-nd-channel": 12,
            "mbed-trace.enable": 0
        },
        "HEXIWEAR": {
            "esp8266-tx": "PTD3",
            "esp8266-rx": "PTD2"
        },
        "NUCLEO_F401RE": {
            "esp8266-tx": "D8",
            "esp8266-rx": "D2"
        },
        "NUCLEO_F411RE": {
            "esp8266-tx": "D8",
            "esp8266-rx": "D2"
        },
        "NUCLEO_F103RB": {
            "esp8266-tx": "D8",
            "esp8266-rx": "D2"
        }
    }
}
```

### 5. modify targets.json file if using Nucleo_F103RB
 Nucleo_F103RB not support LSE and must define LSI.
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set008.png" />
</p>
 After Build Program, check define LSE
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set009.png" />
</p>

### 6. Run Program
<p align="center">
  <img width="60%" src="https://github.com/WIZnet-MbedEthernet/mbed-os-example-sockets_Nucleo-F103RB_W5500/wiki/mbed_set010.png" />
</p>

### 7. Result
**Note:** The default serial port baud rate is 115200 bit/s.

```
Mbed OS Socket example
Mbed OS version: 5.11.2

[EasyConnect] IPv4 mode
[EasyConnect] Using Ethernet WIZnet
[EasyConnect] Init with MAC address
[EasyConnect] DHCP start
[EasyConnect] DHCP completed
[EasyConnect] Connected, IP: 192.168.0.3
[EasyConnect] Connected to Network successfully
[EasyConnect] MAC address 00:XX:XX:XX:XX:XX
[EasyConnect] IP address 192.168.0.3
IP address: 192.168.0.3
Netmask: 255.255.255.0
Gateway: 192.168.0.1
sent 58 [GET / HTTP/1.1]
recv 181 [HTTP/1.1 200 OK]
External IP address: XXX.XXX.XXX.XXX
Done
```