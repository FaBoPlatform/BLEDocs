# iOS連携

テスト用に、iOSアプリは、BLE Utilityを使用します。

| ファイル名 | 概要　 |
| -- | -- |
| hardware.xml | ハードウェア構成を定義 |
| GATT.xml | GATTサービスを定義 |
| bgscript.bgs | BGSCript本体 |
| project.bgproj | プロジェクトを定義 |


## hardware.xml

hardware.xml for Bluegecko
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


GATT.xml for Bluegecko
```
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

        <characteristic uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5035" id="led_on">
            <properties read="true" write="true"/>
            <value >0</value>
        </characteristic>

        <characteristic uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5036" id="led_off">
            <properties read="true" write="true"/>
            <value>0</value>
        </characteristic>
    </service>
    
</configuration>
```

## bgscript.bgs

```
# Boot時に呼ばれる
event system_boot(major ,minor ,patch ,build ,ll_version ,protocol_version ,hw )
    call sm_set_bondable_mode(1)

    call gap_set_adv_parameters( 30, 30, 7 )

    # start advertising
    call gap_set_mode(gap_general_discoverable, gap_undirected_connectable)

    # port setting
    call hardware_io_port_config_direction($0, $FF)
end

# 切断した場合
event connection_disconnected(handle,result)
    
    # restart advertising
    call gap_set_mode(gap_general_discoverable,gap_undirected_connectable)
end

# 値を更新した場合
event attributes_value(connection, reason, handle, offset, value_len, value)

    if handle = led_on
        # LED turn off by input
        call hardware_io_port_write($0, $ff, $03)
    elif handle = led_off
        # LED turn on by input
        call hardware_io_port_write($0, $ff, $00)
    end if

    if value(0:1) = 2 then
        # Write was accepted
        call attributes_user_write_response(connection, 0)
    end if

end
```

