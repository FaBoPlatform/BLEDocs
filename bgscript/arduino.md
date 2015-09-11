# TX(送信)


| PERIPHERAL | Alt | TX | RX  |変数 |
| -- | -- | -- | -- | -- | -- |
|  USART 0 UART | 1 | P0_3 | P0_2 | system_endpoint_uart0 |
|  USART 0 UART | 2 | P1_5 | P1_4 | system_endpoint_uart0 |
|  USART 1 UART | 1 | P0_4 | P0_5 | system_endpoint_uart1 |
|  USART 1 UART | 2 | P1_6 | P1_7 | system_endpoint_uart1 |

hardware.xml

```
<?xml version="1.0" encoding="UTF-8" ?>
<hardware> 
    <sleep enable="false" />
    <sleeposc enable="true" ppm="30" /> 
    <txpower power="15" bias="5" /> 
    <usb enable="false" endpoint="none" /> 
    <script enable="true" />
    <usart channel="0" alternate="1" baud="9600" endpoint="none" flow="true" /> 
    <pmux regulator_pin="7" /> 
</hardware>
```

bgscript
```
event system_boot(major ,minor ,patch ,build ,ll_version ,protocol_version ,hw )
 # UART TX
 call system_endpoint_set_watermarks(system_endpoint_uart0, 1, 0)
 call system_endpoint_tx(system_endpoint_uart0, 13, "BLE113:boot\r\n")


end
```

Arduino Sample
```
#include <SoftwareSerial.h>

SoftwareSerial mySerial(13, 12); // RX, TX

int inByte = 0;  

void setup() {
  Serial.begin(9600);
  mySerial.begin(9600);
}

void loop() {
  if(mySerial.available()>0){
     Serial.write(mySerial.read()); 
  }
  
  delay(10);
}
```

# RX(受信)

hardware.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<hardware> 
    <sleep enable="false" />
    <sleeposc enable="true" ppm="30" /> 
    <txpower power="15" bias="5" /> 
    <usb enable="false" endpoint="none" /> 
    <script enable="true" />
    <usart channel="0" alternate="1" baud="9600" endpoint="none" flow="true" /> 
    <pmux regulator_pin="7" /> 
</hardware>
```


