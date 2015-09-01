# Nordic系BLEモジュール

## Co-processor
ARM® Cortex™ M0

## NRF51822のBlockdiagram(各社モジュール共通)

>![](image/nrf51822.png)

## NRF51822のReferenceデザイン(各社モジュール共通)

>![](image/reference_nrf51822_dd.png)

## 開発環境

nRF51 Software Development Kit 8.0.0
http://developer.nordicsemi.com/nRF51_SDK/nRF51_SDK_v8.x.x/doc/8.0.0/

## MDBT40

### 特徴
* nRF51822にAT7020のチップアンテナを搭載したモデル
* nRF51822をほぼそのまま利用するシンプルな構成
* 開発もNordicのSDKを使う


### 開発環境構築

Nordicのページで開発者登録が必要。
その際開発対象のチップに付属するシリアル番号が必要になる。
チップを登録しないと開発ツールなどのダウンロードができないので注意！

### 書き込み方法

nRF51822向けにはS100というBLEスタックが用意されている。



## BL600

### 特徴
* nRF51822上に独自FWが搭載されている
* smartBasicという言語でプログラミング
* UwTerminalというソフトでFWを制御、書き込み


