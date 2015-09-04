# SoftDevice

## SoftDeviceとは

Nordicが提供しているBLE用のプロトコルスタック。  
S110, S120, S130と３種類あり、それぞれ用途が異なる。

| SoftDevice | 概要 |
| -- | -- |
| S110 | Peripheral専用 |
| S120 | Central/Peripheral両用。  Centralモードの場合は8つ同時接続可能、Peripheralモードの場合はBroadcasterとしても動作する。|
| S130 | Central/Peripheral同時利用。 Centralとして３接続と１つのPeripheralとして動作する。 |
