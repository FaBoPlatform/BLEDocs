# BLEモジュール

BLEモジュールは、国内では「特定無線設備の種別	第２条第１９号に規定する特定無線設備」として定義されている。電波の型式「Ｆ１Ｄ」、周波数は、「2402～2480ＭＨz(２ＭＨz間隔40波)」と定義される。
<hr>
## DA1458X系
<hr>
### Module

dialog社のDA14580は、XiamoiのMiバンドに採用。ARM Cortex M0を内臓。送受信時に最大電流量が4.9mAと、他者に比べ省電力を実現。また、0.9Vの低電圧で動作可能である。

| モジュール名 | BLE Chip　| Ver | メーカー | 技適 | 最大送信出力|受信感度|TX最大電流|スリープモード|
| -- | -- | -- |-- |-- |
| [Type ZY](http://www.murata.co.jp/products/microwave/module/bluetoothmodule/schematic/typez.html#tab) | DA14580 | 4.1 | [Murata](http://www.murata.co.jp/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=001&TC=G&PK=1&FN=387tele&SN=%8F%D8%96%BE&LN=32&R1=*****&R2=*****) |0dBm||4.8mA|0.6uA|
|[PAN1740](http://eu.industrial.panasonic.com/products/wireless-connectivity/bluetooth/bluetooth-smart-low-energy/series/pan1740/CS464/model/ENW89846A1KF) | DA14580 | 4.1 | [Panasonic](http://eu.industrial.panasonic.com/)|未|0dBm|-93dBm|4.9mA|<1uA|


この他、[AvantWave](http://www.avantwave.com/)もパートナーになっているが、製品概要は現時点で公開されていない。
<hr>
## CC254x系
<hr>
### Module

| モジュール名 | BLE Chip　| Ver | メーカー | 技適 | 最大送信出力|受信感度|TX最大電流|スリープモード|
| -- | -- | -- |-- |-- |
| [BLE113](https://www.bluegiga.com/en-US/products/ble113-bluetooth-smart-module/) | CC2541 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=352ul&SN=%94F%8F%D8&LN=3&R1=*****&R2=*****) |0dBm|-93dBm|18.2mA|0.4uA|
| [BLE112](https://www.bluegiga.com/en-US/products/ble112-bluetooth-smart-module/) | CC2540 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=209&TC=N&PK=1&FN=022acb&SN=%94%46%8F%D8&LN=2&R1=*****&R2=*****) |+3dBm| -92dBm|27mA|0.4uA|
|[cB-OLP425i-04](http://support.connectblue.com/display/PRODBTSPA/cB-OLP425+cB-OLS425+cB-OLS426+Electrical+Mechanical+Data+Sheet)|CC2540|4.0|[connectBlue](http://www.connectblue.com/home/)|[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=204&TC=N&PK=1&FN=158test&SN=%94%46%8F%D8&LN=21&R1=*****&R2=*****)|||||
| [BLE121LR](https://www.bluegiga.com/en-US/products/ble121lr-bluetooth-smart-long/) | CC2541 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](https://www.bluegiga.com/en-US/download/?file=eQs1EzP8S9KiSLoED4OyjA&title=BLE121LR%2520Japan%2520Report%2520and%2520Certificate&filename=BLE121LR_Japan.zip)* |+8dBm| -98dBm|36mA<br>25 mA (DC/DC)| 0.5uA|
|[PAN1721](http://na.industrial.panasonic.com/products/wireless-connectivity/bluetooth/bluetooth-smart-low-energy/series/pan1721-series/CS465)|CC2541|4.0|[Panasonic](http://wwww.panasonic.com)| 未|0dBm|-96dBm|14 mA|0.5uA|
|[SESUB-PAN-T2541](http://product.tdk.com/ja/products/sesub/pan/catalog/)|CC2541|4.0|[TDK](http://product.tdk.com/)||0dBm||20.6mA|1.2uA|
|[LBM313](https://punchthrough.com/products/lbm313-module/)|CC2541||[punchthrough](https://punchthrough.com/products/) |||

* BLE121LRは、[ACB,Inc](http://acbcert.com/MIC-Japanese-Radio-Certification-services.asp)が認証をおこなっているが、総務省のDBに未反映

### USB
| モジュール名 | BLE Chip　| Ver| メーカー | 技適 | 最大送信出力|受信感度|TX最大電流|スリープモード
| -- | -- | -- |-- |-- |
| [BLED112](https://www.bluegiga.com/en-US/products/bled112-bluetooth-smart-dongle/) | CC2540 | 4.0 | [Bluegiga](http://www.bluegiga.com/) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=003&TC=N&PK=1&FN=316dspr&SN=%94%46%8F%D8&LN=30&R1=*****&R2=*****) |0dBm|-93dBm||||

## <hr>NRF51822系
<hr>
### Module

| モジュール名 | BLE Chip　| Ver| メーカー | 技適 | 最大送信出力|受信感度|TX最大電流|スリープモード
| -- | -- | -- |-- |-- |
| [RFD22301](http://www.rfdigital.com/product/rfd22301-rfduino-ble-smt/index.html) | NRF51822 | 4.0 | [RFDigital](http://www.rfdigital.com/) | 未 |+4dBm||||
|[BL620](http://www.lairdtech.com/products/bl620) | NRF51822 | 4.0 | [Laird](http://www.lairdtech.com) | 未 |+4dBm||||
| [BL600-SA](http://www.lairdtech.com/products/bl600-series) | NRF51822 | 4.0 | [Laird](http://www.lairdtech.com) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=204&TC=N&PK=1&FN=150test&SN=%94%46%8F%D8&LN=28&R1=*****&R2=*****)| +4dBm|-91dBm|||
| [BL600-SC](http://www.lairdtech.com/products/bl600-series) | NRF51822 | 4.0 | [Laird](http://www.lairdtech.com) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=204&TC=N&PK=1&FN=150test&SN=%94%46%8F%D8&LN=29&R1=*****&R2=*****)| +4dBm|-91dBm|||
| [BL600-ST](http://www.lairdtech.com/products/bl600-series) | NRF51822 | 4.0 | [Laird](http://www.lairdtech.com) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=204&TC=N&PK=1&FN=150test&SN=%94%46%8F%D8&LN=27&R1=*****&R2=*****)| +4dBm|-91dBm|||
| [HRM1017](http://www.hosiden.co.jp/news/product/hrm1017.html) | NRF51822 | 4.0 | [Hoshiden](http://www.hosiden.co.jp/) |[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=349ul&SN=%94%46%8F%D8&LN=16&R1=*****&R2=*****)| +4dBm||||
|[HRM1026](http://www.hosiden.co.jp/news/product/hrm1026.html) | NRF51822 | 4.0 | [Hoshiden](http://www.fcl.fujitsu.com/) | | 4dBm||||
| [BVMCN5102](http://www.braveridge.com/Specification%20Documents/BVMCN5102-BK%20Spec%20sheet%20Ver101.pdf) | NRF51822 | 4.0 | [Braveridge](http://www.braveridge.com/)  |[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=370ul&SN=%94%46%8F%D8&LN=3&R1=*****&R2=*****)|+4dBm||||
|[SY-MN1319X1](http://www.sysgration.com/webe/html/products/index2.aspx?num=236)| NRF51822 |4.0| [Sysgration](http://www.sysgration.com/) | 未 | +4dBm |  | 10.5mA<br>@0dBm | 3.5uA |
|[EYSFCNZXX](https://www.yuden.co.jp/jp/solutions/ble/product/) | NRF51822 | 4.0 | [TAIYO YUDEN](https://www.yuden.co.jp) | [済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=001&TC=N&PK=1&FN=358tele&SN=%94%46%8F%D8&LN=91&R1=*****&R2=*****) |||||
|[BTS01](http://www.smk.co.jp/products/series_outline/Bluetooth_Module/?sid=13288&seni=&youto=&karamu=hinban&sort=asc&no=10&tp=) | NRF51822 | 4.1 | [SMK](http://www.smk.co.jp/)|[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=365ul&SN=%94%46%8F%D8&LN=9&R1=*****&R2=*****)|||||
| [MDBT4.0](http://www.raytac.com/products.php)| NRF51822 | 4.1 | [Raytac](http://www.raytac.com/) | | +4dBm|-93dBm|||
| [MDBT4.0 nano](http://www.raytac.com/products.php) | NRF51822 | 4.1 | [Raytac](http://www.raytac.com/) | | +4dBm|-93dBm|||
| [BMD-200](https://www.rigado.com/product/bmd-200) | NRF51822 | 4.1 | [RIGADO](http://www.rigado.com/) | | +4dBm|-93dBm|16mA||
| [MBH7BLZ02](http://www.fcl.fujitsu.com/downloads/services/wireless-modules/mbh7blz01.pdf) | NRF51822 | 4.1 | [富士通コンポーンエント](http://www.fcl.fujitsu.com/) |[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=363ul&SN=%94F%8F%D8&LN=7&R1=*****&R2=*****) | 4dBm|-88dBm|12mA|5uA|
|[BVMCN5103](http://www.braveridge.com/Specification%20Documents/BVMCN5103-BK%20Spec%20sheet%20Ver1.0J.pdf)| NRF51822 | 4.1 | [Braveridge](http://www.braveridge.com/) |[済](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=007&TC=N&PK=1&FN=370ul&SN=%94%46%8F%D8&LN=3&R1=*****&R2=*****)|+4dBm||||
|[BlueMod+S](http://www.stollmann.de/en/modules/bluetooth-modules-21-and-40/bluemod-s.html)|NRF51822|4.1|[stollmann](http://www.stollmann.de/en/modules/bluetooth-modules-21-and-40/bluemod-s.html)|未|+4dBm|-88dBm||4uA|
<hr>
## CSR101x系
<hr>
### Module
| モジュール名 | BLE Chip　| Ver| メーカー | Web | 最大送信出力|受信感度|TX最大電流|スリープモード
| -- | -- | -- |-- |-- |
| [RN4020](http://ww1.microchip.com/downloads/en/DeviceDoc/50002279A.pdf) | CSR2012 | 4.0 | [Microchip](http://www.microchip.com/) |  |+7dBm||||
<hr>
## BlueNGR系
<hr>
### Module
| モジュール名 | BLE Chip　| Ver| メーカー | Web | 最大送信出力|受信感度|TX最大電流|スリープモード
| -- | -- | -- |-- |-- |
| [BMD-200](https://www.rigado.com/product/bmd-100) | BlueNGR | 4.1 | [RIGADO](http://www.rigado.com/) | | +8dBm|-88dBm|16mA|||
<hr>
## BCM20732系
<hr>
### Module
| モジュール名 | BLE Chip　| Ver| メーカー | Web | 最大送信出力|受信感度|TX最大電流|スリープモード
| -- | -- | -- |-- |-- |
| [EMRF-20732S](http://www.embeddedmasters.com/ProductDetail/EMRF20732S-Embedded-Masters/552437/#.VSihgo7tmko) | BCM20732| EmbeddedMaster |  |  | | |||


<hr>
## MK7105系
<hr>
### Module

| モジュール名 | BLE Chip |メーカー | Web | 最大送信出力|受信感度|
| -- | -- | -- |
| [MK71050-03](http://www.lapis-semi.com/jp/semicon/telecom/landing/mk71050-03.html) | MK7105 | [Lapis](http://www.lapis-semi.com/) |  |0dBm|-86dBm

# 技適

* [技術基準適合証明等の公示（平成26年度分）](http://www.tele.soumu.go.jp/j/ref/material/tech/index.htm)
* [適合性評価機関等の情報](http://www.tele.soumu.go.jp/j/sys/equ/mra/ninsyoukikan/index.htm#ninteihyouka)
* [技術基準適合証明等を受けた機器の検索](http://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jk01)


