# TI系BLEモジュール

## Co-processor
8051

## 開発者サイト

開発用のSDKは、モジュールメーカーのものを使用する。

https://www.bluegiga.com/en-US/support/

## 開発に必要なハードウェア



### TI提供ツール
| 必要なもの | 提供先 |
| -- | -- |
|デバッカ | [CC-Debugger](http://www.tij.co.jp/tool/jp/cc-debugger) |
|ソフトウェア|[FLASH-PROGRAMMER(1の方)](http://www.tij.co.jp/tool/jp/flash-programmer)|

### 各社開発ボード

| ボード名 | 提供先 |
| -- | -- |
| [CC2541 SensorTag 開発キット](http://www.tij.co.jp/tool/jp/cc2541dk-sensor#1) | TI |
| [DKBLE](https://www.bluegiga.com/en-US/products/ble113-bluetooth-smart-module/#devkits) | Bluegiga|

## CC254X搭載モジュール


| モジュール名 | BLE Chip　| Ver | メーカー | 技適 | 最大送信出力|受信感度|TX最大電流|スリープモード|
| -- | -- | -- |-- |-- |
| [BLE113](https://www.bluegiga.com/en-US/products/ble113-bluetooth-smart-module/) | CC2541 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=352ul&SN=%94F%8F%D8&LN=3&R1=*****&R2=*****) |0dBm|-93dBm|18.2mA|0.4uA|
| [BLE112](https://www.bluegiga.com/en-US/products/ble112-bluetooth-smart-module/) | CC2540 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=209&TC=N&PK=1&FN=022acb&SN=%94%46%8F%D8&LN=2&R1=*****&R2=*****) |+3dBm| -92dBm|27mA|0.4uA|
|[cB-OLP425i-04](http://support.connectblue.com/display/PRODBTSPA/cB-OLP425+cB-OLS425+cB-OLS426+Electrical+Mechanical+Data+Sheet)|CC2540|4.0|[connectBlue](http://www.connectblue.com/home/)|[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=204&TC=N&PK=1&FN=158test&SN=%94%46%8F%D8&LN=21&R1=*****&R2=*****)|||||
| [BLE121LR](https://www.bluegiga.com/en-US/products/ble121lr-bluetooth-smart-long/) | CC2541 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](https://www.bluegiga.com/en-US/download/?file=eQs1EzP8S9KiSLoED4OyjA&title=BLE121LR%2520Japan%2520Report%2520and%2520Certificate&filename=BLE121LR_Japan.zip)* |+8dBm| -98dBm|36mA<br>25 mA (DC/DC)| 0.5uA|
|[PAN1721](http://na.industrial.panasonic.com/products/wireless-connectivity/bluetooth/bluetooth-smart-low-energy/series/pan1721-series/CS465)|CC2541|4.0|[Panasonic](http://wwww.panasonic.com)| 未|0dBm|-96dBm|14 mA|0.5uA|
|[SESUB-PAN-T2541](http://product.tdk.com/ja/products/sesub/pan/catalog/)|CC2541|4.0|[TDK](http://product.tdk.com/)||0dBm||20.6mA|1.2uA|

## CC254X搭載モジュールのBlock diagram
> BLE113 DATA SHEETより抜粋
![](image/block_ble113.png)
> BLE112 DATA SHEETより抜粋
>![](image/block_ble112.png)
> BLE121LR DATA SHEETより抜粋
>![](image/block_ble121.png)

## 各モジュールのReferenceデザイン
### BLE113,112,121
> BLE113 DATA SHEETより抜粋
![](image/refarence_ble113.png)
> BLE112 DATA SHEETより抜粋
>![](image/refarence_ble112.png)
> BLE121LR DATA SHEETより抜粋
>![](image/refarence_ble121.png)



