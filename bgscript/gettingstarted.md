# BGScript入門

## HelloLED

```
<?xml version="1.0" encoding="UTF-8" ?>

<hardware>
</hardware>
```



```
event system_boot(major, minor, patch, build, ll_version, protocol_version, hw)
    # 0000 0011 $03 P0_0,P0_1をenableに
    call hardware_io_port_config_direction($0,$03)
    
    # 0000 0011 $03 をHIGHに
    call hardware_io_port_write($0,$03,$03)
end
```

hardware_io_port_writeでは、($0,$03,$03)の記述で、
P0_0, P0_1 $03 (0000 0011)に関して、$03(000 0011)の値を送っている。

C:\Bluegiga\ble-1.2.1-91\example\test　のproject.bgprojファイルを任意テキストエディタ（メモ帳以外）で開く。

```
<script in="battery.bgs" />
```
から
```
<script in="ledtest.bgs" />
```
と変更し保存する。

## 実機への転送

C:\Bluegiga\ble-1.2.1-91\example\test　のBLE113-project.bgprojファイルを実行する。

[](bgscript003.png)