#BLED１１２の焼き込み


## ソフトウェアの準備


「Bluetooth Smart Software and SDK」の最新バージョンをダウンロード
(記入時点の最新版はv.1.3.2）
https://www.bluegiga.com/en-US/products/bled112-bluetooth-smart-dongle/

## 焼き込み準備
焼き込みを行うため、BLED112に対してDFUモードで接続する


ダウンロードしたファイルを展開し、binフォルダ内に格納されている「blegui2.exe」起動する

BLED112をUSBポートに接続し、GUIToolにて対象のポートを選択する
<br>
![](bled112_001.jpg)

「Attach」ボタン押下で接続後、メニューの「Commands」より「DFU」を選択する
<br>
![](bled112_002.jpg)

DFUのウィンドウにて、初期状態で選択されている「USB Bootloader」タブを選択し、「Boot Into DFU mode」ボタンを押下する
<br>
![](bled112_003.jpg)

ここでドライバが必要になる場合、ダウンロードしたファイルから「windrv」フォルダ内にある「dfu.ini」を指定してインストール

DFUモードにて接続が完了すると、画面上の「Connected」から「Disconnected」に変更される
![](bled112_004.jpg)

デバイスマネージャにて確認
![](bled112-005.jpg)

## 焼き込みを行うデータの作成
