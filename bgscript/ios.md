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

        <characteristic uuid="2a00">
            <properties read="true" const="true" />
            <value>BLE113 LED Sample</value>
        </characteristic>
        
    </service>
    
    <service uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5034">
        <description>LED Access</description>

        <characteristic uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5035" id="led_on">
            <properties read="true" write="true" notify="true"/>
            <value >0</value>
        </characteristic>

        <characteristic uuid="3DDEE461-8D54-4CD5-89F5-1C85F88B5036" id="led_off">
            <properties read="true" write="true" notify="true"/>
            <value>0</value>
        </characteristic>
    </service>
    
</configuration>
```


