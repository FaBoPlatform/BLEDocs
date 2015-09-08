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
| Profile | UUID |
| -- | -- |
| Generic Access Profile | 0x1800 | 
| Generic Attribute Profile | 0x1801 |

### GATT 属性タイプ


```

```


