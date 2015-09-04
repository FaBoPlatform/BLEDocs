# BGAPI

Node.jsのSerialPortを用いてBLED112を制御する方法の解説です。

## Node.jsのインストール
Node.jsをインストールします。

http://nodejs.org/

## SerialPortライブラリのインストール
```
$ npm install serialport
```

## サンプルの作成

```
var serialport = require("serialport");
 
var SerialPort = serialport.SerialPort;
 
var sp = new SerialPort("/dev/tty.usbmodem1", { // ここのパスは適宜変更する
 
    baudrate: 115200,
}, false);

sp.open(function () {
    console.log('open');
    
    sp.on('data', function(data) {
     // [0,0,0,1]を受信すれば成功
        for(i=0; i<data.length; i++) {
         console.log(i+': ' + data[i].toString(16));
  }
    });
    
    var sendData = new Uint8Array([0,0,0,1]); // Helloコマンド
//     var sendData = new Uint8Array([0,2,6,1,2,2]); // アドバタイズ開始コマンド
 // コマンド送信
    sp.write(sendData, function(err, results) {
        console.log('err ' + err);
        console.log('results ' + results);
    });
});
```

接続されているシリアルポート名は下記コマンドで調べられます。
ドングルを接続した状態でコマンドを実行してみましょう。

```
$ ls /dev/tty.*
```

## BGAPIのコマンド

簡単に説明するとHelloコマンドという動作確認用のBGAPIをnode.jsからBLED112に送信しています。リファレンスには下記の様に書いてあるので「0,0,0,1」を送ります。

Command

| Byte | Type | Name | Description |
| -- | -- | -- | -- |
| 0 | 0x00 | hilen | Message type:command |
| 1 | 0x01 | lolen | Minimum payload length |
| 2 | 0x02 | class | Message Class:System |
| 3 | 0x03 | method | Message ID |

返事は下記の様に「0,0,0,1」が返って来れば成功となります。

Response

| Byte | Type | Name | Description |
| -- | -- | -- | -- |
| 0 | 0x00 | hilen | Message type:response |
| 1 | 0x01 | lolen | Minimum payload length |
| 2 | 0x02 | class | Message Class:System |
| 3 | 0x03 | method | Message ID |

同様に「0,2,6,1,2,2」を送信すればアドバタイズが開始されますので、BLEデバイスから検索する事ができるようになります。

BGAPIの詳細は「Bluetooth_Smart_Software_vX.X_API_Reference」を参照してください。
