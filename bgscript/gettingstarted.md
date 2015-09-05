# BGScript入門

## HelloLED

| ファイル名 | 概要　 |
| -- | -- |
| hardware.xml | ハードウェア構成を定義 |
| GATT.xml | GATTサービスを定義 |
| bgscript.bgs | BGSCript本体 |
| project.bgproj | プロジェクトを定義


## hardware.xml

hardware.xml
```
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
</hardware>
```
hardware.xml for Bluegiga
```
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
    <sleeposc enable="true" ppm="30" />
    <script enable="true" />
</hardware>
```
## GATT.xml

GATT.xml for BlueGecko
```
<?xml version="1.0" encoding="UTF-8"?>

<gatt>
</gatt>
```

GATT.xml for Bluegiga
```
<?xml version="1.0" encoding="UTF-8"?>

<configuration>

 <service uuid="1800">
        <description>Generic Access Profile</description>

        <characteristic uuid="2a00">
            <properties read="true" const="true" />
            <value>BLE113 LED Sample</value>
        </characteristic>

        <characteristic uuid="2a01">
            <properties read="true" const="true" />
            <value type="hex">0000</value>
        </characteristic>
 </service>

</configuration>
```
## BGScript

bgscript.bgs for Bluegecko
```
# Boot event listener - Generated when the module is powered up or reset
event system_boot(major, minor, patch, build, bootloader, hw)
    # Init GPIO PIN
	call hardware_configure_gpio(5,6,hardware_gpio_mode_push_pull,1)
	call hardware_configure_gpio(5,7,hardware_gpio_mode_push_pull,1)
	
    # LED On $40(0100 0000->6pin)
    call hardware_write_gpio(5,$40,$00)
	# LED On $80(1000 0000->7pin)
	call hardware_write_gpio(5,$80,$00)
end
# End of BGScript
```

bgscript.bgs for Bluegiga
```
dim i
dim pos
event system_boot(major ,minor ,patch ,build ,ll_version ,protocol_version ,hw )
  call hardware_io_port_config_direction($0, $ff)

 call hardware_io_port_write($0, $ff, $00)
 call hardware_set_soft_timer(32768,1,0)
end


event hardware_soft_timer(handle)
 if handle = 1 then
 pos = 1<<i
 call hardware_io_port_write($0, $ff, pos)
 i = i + 1
 if i > 1 then
 i = 0
 end if
 end if
end
```
## bgprojファイル

project.bgproj for BlueGecko
```
<?xml version="1.0" encoding="UTF-8" ?>

<!-- Project file for BGM111 Bluetooth Smart module -->
<project device="bgm111">

	<!-- GATTサービスデータベース -->
	<gatt in="GATT.xml" />
	
	<!-- ハードウェアの設定 -->
    <hardware in="hardware.xml" />
    
	<!-- BGScript本体 -->
	<scripting>
		<script in="bgscript.bgs" />
    </scripting>
	
	<!-- Firmware output file -->
	<image out="helloLED.bin" />
   
</project>
```

project.bgproj for Bluegiga
```
<?xml version="1.0" encoding="UTF-8" ?>

<project>
    <device type="ble113"/>
    <boot fw="bootuart" />

    <!-- GATT service database -->
    <gatt in="GATT.xml" />
	
    <!-- Local hardware configuration file -->
    <hardware in="hardware.xml" />
    
    <!-- BGScript source code -->
    <script in="bgscript.bgs" />
 
    <!-- Firmware output file -->
    <image out="helloLED.bin" />
  
</project>
```

## 実機への転送 for BlueGecko

BGToolで実機へ転送する

![](bgtool002.png)

## 実機への転送 for Bluegiga

