# パケットスニファの設定

## 必要なハード

* nRF51822EvaluationKit(PCA10001)
* nRF51822DevelopmentKitdongle(PCA10000)
* nRF51422EvaluationKit(PCA10003)v3.0.0以降
* nRF51422DevelopmentKit(PCA10028)v1.0以降


## 必要なソフト

* Windows7以降 （Mac上のViertualBoxでは動作しませんでした）
* [nRFgoStudio](https://www.nordicsemi.com/eng/Products/Bluetooth-Smart-Bluetooth-low-energy/nRF51822)
* [nRF-Sniffer](https://www.nordicsemi.com/eng/Products/Bluetooth-Smart-Bluetooth-low-energy/nRF51822)
* [Wireshark](https://www.wireshark.org/download.html) v1.10.1以降


## 準備

1. nRFgoStudioをインストールします。
2. 対応ハードをUSBに接続します。
3. スニファ対象のBLE機器を周辺で作動させます。
4. nRF-Snifferのzipを解凍します。
5. nRFgo Studioを起動します。
6. 左のDeviceManagerから接続した機器を選びます。
7. 「Erase all」をクリックして既存のファームを削除します。
8. Program Applicationのタブを選択します。
9. BrowseからnRF-SnifferのFirmwareフォルダ内のhexファイルを選択します。
10. Program でファームを書き込みます。
11. 接続しているBLE機器はパケット受信時にLEDが点灯するようになります。
12. Wiresharkをインストールします。

![](sniffer01.png)


## スニフ


1. ble-sniffer_xxx_Sniffer.exe を起動します。
2. コマンドラインのメニューが表示されます。
3. 中段に使用可能なコマンド、下段に検出されたデバイス一覧が表示されます。

![](sniffer02.png)

4. 上下キーでカーソルを移動し、Enterキーで対象デバイスを選択します。
5. wキーでWiresharkが起動します。
6. 選択したデバイスのパケット詳細が表示されます。


![](sniffer03.png)