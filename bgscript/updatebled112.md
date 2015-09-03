#BLED１１２の焼き込み

BLED112の焼き込みは、CCDebuggerを使用せず、直接Windowsマシンに接続して行います。


## 環境設定

「Bluetooth Smart Software and SDK」の最新バージョンをダウンロードする。
(記入時点の最新版はv.1.3.2）
<br>
https://www.bluegiga.com/en-US/products/bled112-bluetooth-smart-dongle/

<br>
ダウンロードしたファイルを展開し、binフォルダ内に格納されているBLE GUI tool「blegui2.exe」起動する。
<br>
BLED112をUSBポートに接続し、BLE GUI ToolにてBLED112が接続されているポートを選択する。
<br>
![](bled112_001.jpg)

「Attach」ボタン押下でBLED112と接続後、メニューの「Commands」より「DFU」を選択する。
<br>
![](bled112_002.jpg)

DFUのウィンドウにて、初期状態で選択されている「USB Bootloader」タブを選択し、「Boot Into DFU mode」ボタンを押下する。
<br>
![](bled112_003.jpg)
<br>
※ここでドライバが必要になる場合、ダウンロードしたファイルから「windrv」フォルダ内にある「dfu.ini」を指定してインストールする。

DFUモードにて接続が完了すると、画面上の「Connected」から「Disconnected」に変更される。
![](bled112_004.jpg)

デバイスマネージャにて下の図のようになっていることを確認する。
![](bled112-005.jpg)

## 焼き込みデータの作成

作成したファイルに以下の内容を追記する


### 1.焼き込みに必要な条件


bgprojファイル
```
<config in="config.xml" />
```

hardware.xml
```
<script enable="true" />
```


config.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<config>
    <script force="true" />
</config>
```
<br>
### 2.DFUモードに遷移する条件（例）

この例では外部からのアクセスで簡単にできてしまうのでテスト用として使用すること

**※DFUモードに遷移する条件を追加しておかないと再度焼き込みを行うことが出来なくなってしまうので注意！
**

gatta.xml
```
    <!-- custom service for allowing DFU-mode reboots -->
    <service uuid="4f3edfe7-6f17-4f87-b2ee-ea2cdac0dd02">
        <description>DFU Reboot Service</description>
        
        <!-- custom characteristic for allowing DFU-mode reboots -->
        <characteristic uuid="590c4bd9-b5e2-4a1a-867e-9b033ed1eadb" id="c_dfu_reboot_trigger">
            <description>DFU Reboot Trigger</description>
            <properties write="true" />
            <value length="1" />
        </characteristic>
        
    </service>
```
<br>
bgsファイル
```
event attributes_value(connection, reason, handle, offset, value_len, value_data)
    if handle = c_dfu_reboot_trigger then
        call system_reset(1)
    end if
end
```


## Hexファイルの作成

コマンドプロンプトを起動し、bgprojファイルがある場所に移動して下記のコマンドを実行する(bgbuild.exeの場所やbgprojの格納場所によって変更する)
```
c:¥bluegiga¥ble-1.3.2-122/bin\bgbuild.exe project.bgproj
```

##焼き込み
Selected Firmware fileの項目にてhexファイルを選択し、Uploadボタンを押下する
<br>
![](bled112_006.jpg)

logに「Finish」が表示されたら完了
<br>
![](bled112_007.jpg)