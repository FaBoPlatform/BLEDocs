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



hardware.xml for Bluegiga
```
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
    <sleeposc enable="true" ppm="30" />
    <script enable="true" />
</hardware>
```