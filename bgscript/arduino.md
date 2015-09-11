

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

