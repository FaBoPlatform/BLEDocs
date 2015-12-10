# 開発環境(nRF52)

# nRF52使ったプログラムの作成方法 

## 使用した環境
* MDK-Lite Ver. 5.16a
* Windows 7
* nRF52 Development Kit (PCA10040)

## 手順

手順はほぼnRF51と同じなので、詳細は[コチラ](https://www.gitbook.com/book/fabo/bledocs/edit#/edit/master/nordic/dev802.md)を参照。
現状(2015/12)ではまだPreviewなのでPackは用意されていない模様。
なので、ソースを自分でプロジェクトにコピーする必要がある。


### Application作成

1. Keil uVision5を起動する

2. uVision5のProjectメニューから新たにプロジェクトを作成する

3. Deviceの設定を聞かれるのでSofware PacksのnRF52832_xxAAを選択する
  ![](sc01.png)

4. 必要なPackをインストールする  
 4.1. DeviceのStartupを選択し、Bootに必要なプログラムをインストールする  
  ![](sd109.png)

3. 設定を変更する  

 3.1. Options for Targetを選択する  
  ![](sd008.png)  


 3.6. JLinkの設定を変更する
    * "Reset and Run"をチェックし、書き込み時にリセット＆実行を行う
   ![](sd108.png)
 
4. 必要なPackをインストールする  
 4.1. Manage Run-Time Environmentを選択する  
  ![](sd006.png)  
 4.2. DeviceのStartupを選択し、Bootに必要なプログラムをインストールする  
  ![](sd109.png)

5. Applicationを作成する  
 5.1. Project内のグループ名(今回はApplication)を右クリックし、"Add New Item to.."を選択する
  ![](sd110.png)
 5.2. main.cを作成する
  ![](sd111.png)
 5.3. 今回は無機能のApplicationなので、空のmain文のみにする

  ```int main() {  
  }
  ```

6. ビルドして実機にダウンロードする  
 6.1. ビルドボタンをクリックするとビルドされます  
 ![](sc112.png)
 
 6.2. LOADボタンを押すとSoftDeviceの書き込みが開始されます  
 ![](sd013.png)

