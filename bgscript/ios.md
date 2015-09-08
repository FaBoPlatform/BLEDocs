# iOS連携

テスト用に、iOSアプリは、BLE Utilityを使用します。

| ファイル名 | 概要　 |
| -- | -- |
| hardware.xml | ハードウェア構成を定義 |
| GATT.xml | GATTサービスを定義 |
| bgscript.bgs | BGSCript本体 |
| project.bgproj | プロジェクトを定義 |


## hardware.xml


hardware.xml for Bluegiga
```xml
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
    <sleeposc enable="true" ppm="30" />
    <script enable="true" />
</hardware>
```

hardware.xml for Bluegecko
```xml
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
</hardware>
```


## GATT.xml

UUIDの生成は、OS Xではuuidgenで生成する

```
$ uuidgen
3DDEE461-8D54-4CD5-89F5-1C85F88B5034
```

### GATT Service
| Service | UUID |
| -- | -- |
| Generic Access Profile | 0x1800 | 
| Generic Attribute Profile | 0x1801 |

### GATT 特性タイプ
| 属性タイプ | UUID |
| -- | -- |
| Device Name | 0x2A00 | 
| Appearance | 0x2A01 |
| Peripheral Privacy Flag | 0x2A02 |
| Reconnection Address | 0x2A03 |
| Peripheral Preferred Connection Parameters | 0x2A04 |
| Service Changed | 0x2A05 |


GATT.xml for Bluegiga
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration>
    <service uuid="1800">
        <description>Generic Access Profile</description>

        <characteristic uuid="2A00">
            <properties read="true" const="true" />
            <value>BLE113 LED Sample</value>
        </characteristic>
        
    </service>
    
    <service uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5034">
        <description>LED Access</description>

        <characteristic uuid="0001" id="xgatt_ledon">
            <properties read="true" write="true"/>
            <value >0</value>
        </characteristic>

        <characteristic uuid="0002" id="xgatt_ledoff">
            <properties read="true" write="true"/>
            <value>0</value>
        </characteristic>
    </service>
    
</configuration>
```

GATT.xml for Bluegecko
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<gatt>
    <service uuid="1800">
        <description>Generic Access Profile</description>

        <characteristic uuid="2A00">
            <properties read="true" const="true" />
            <value>BLE113 LED Sample</value>
        </characteristic>

    </service>

    <service uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5034">
        <description>LED Access</description>

        <characteristic uuid="0001" id="xgatt_ledon">
            <properties read="true" write="true" indicate="true"/>
            <value type="hex" length="1">0</value>
        </characteristic>

        <characteristic uuid="0002" id="xgatt_ledoff">
            <properties read="true" write="true" const="true"/>
            <value type="hex" length="1">0</value>
        </characteristic>
    </service>

</gatt>
```


## bgscript.bgs for Bluegiga

```c
# Boot時に呼ばれる
event system_boot(major ,minor ,patch ,build ,ll_version ,protocol_version ,hw )
    
	# アドバータイジングのパラメータ
    call gap_set_adv_parameters( 30, 30, 7 )

    # アドバータイジング
    call gap_set_mode(gap_general_discoverable, gap_undirected_connectable)

    #　LEDポートの設定
    call hardware_io_port_config_direction($0, $FF)
	call hardware_io_port_write($0, $ff, $00)

end

# 切断した場合
event connection_disconnected(handle,result)

	# アドバータイジングを再開する
    call gap_set_mode(gap_general_discoverable,gap_undirected_connectable)

end

# 値を更新した場合
event attributes_value(connection, reason, handle, offset, value_len, value)

	# LED turn off by input
    if handle = xgatt_ledon then 
        call hardware_io_port_write($0, $ff, $03)
	# LED turn on by input
    end if 
	if handle = xgatt_ledoff then 
        call hardware_io_port_write($0, $ff, $00)
    end if

    if value(0:1) = 2 then
        # レスポンスを返す
        call attributes_user_write_response(connection, 0)
    end if
	
end

```

bgscript.bgs for Bluegecko
```c
dim result

# Boot時に呼ばれる
event system_boot(major, minor, patch, build, bootloader, hw)
    
	# アドバータイジングのパラメータ
    call le_gap_set_adv_parameters( 30, 30, 7 )

    # アドバータイジング
    call le_gap_set_mode(le_gap_general_discoverable, le_gap_undirected_connectable)

    #　LEDポートの設定
    call hardware_configure_gpio(5,6,hardware_gpio_mode_push_pull,1)
    call hardware_configure_gpio(5,7,hardware_gpio_mode_push_pull,1)
end

# 切断した場合
event le_connection_closed(reason,connection)

	# アドバータイジングを再開する
    call le_gap_set_mode(le_gap_general_discoverable,le_gap_undirected_connectable)

end

# Generated when GATT characteristic client configuration value is changed
event gatt_server_characteristic_status(connection,characteristic,status_flags,client_config_flags) 
	
end 

# 値を更新した場合
event gatt_server_attribute_value(connection,characteristic,att_opcode,offset,value_le,value)
	
	if characteristic = xgatt_ledon then 
		call hardware_write_gpio(5, $40, $00)
		call gatt_server_write_attribute_value(xgatt_ledon, 0, 1, value(0:value_le))(result)
		call gatt_server_send_characteristic_notification(connection, xgatt_ledon, 1, value(0:value_le))(result)
	end if
	
	if characteristic = xgatt_ledoff then 
		call hardware_write_gpio(5, $40, $40)
		call gatt_server_write_attribute_value(xgatt_ledoff, 0, 1, value(0:value_le))(result)
		call gatt_server_send_characteristic_notification(connection, xgatt_ledoff, 1, value(0:value_le))(result)
	end if	
	
end

```


## Project.proj

Project.bgproj for Bluegiga
```xml
<?xml version="1.0" encoding="UTF-8" ?>

<project>
    <!-- Device Type -->
    <device type="ble113"/>

    <!-- GATT service database -->
    <gatt in="GATT.xml" />

    <!-- Local hardware configuration file -->
    <hardware in="hardware.xml" />

    <!-- BGScript source code -->
    <script in="bgscript.bgs" />

    <!-- Firmware output file -->
    <image out="iOSSample.bin" />

</project>
```

Project.bgproj for Bluegecko
```xml
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
    <image out="iOSSample.bin" />

</project>
```
