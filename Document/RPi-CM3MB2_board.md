## RPi-CM3MB2 各部名称と説明  
### 1. 基板構成  
製品基板の各部名称は以下のとおりです。

![board](/Image/Board_pic/CM3MB2_board.png)

| No | 名称 | No | 名称 |
|:-----:|:-----|:-----:|:-----|
|1|microSDスロット|2|CAMERAコネクタ|
|3|シャットダウン LED |4|ステータス LED |
|5|電源 LED|6|内部配線用 LED接続7PIN ZHコネクタ|
|7|USB Type A コネクタ|8|電源 ON / OFF 用スイッチ|
|9|内部配線用 電源スイッチ接続 3PIN PHコネクタ|10|Li-ionバッテリー接続用 2PINコネクタ|
|11|200PIN DDR-SODIMM ソケット|12|40PIN ピンヘッダー GPIOコネクタ|
|13|12PIN ピンヘッダー 拡張GPIOコネクタ|14|メイン基板接続用コネクタ|
|15|バックアップ電源用Li-ion電池ホルダー|16|RTCバックアップ用 CR2032 電池ホルダー|
|17|USB Bootモード設定用 3PINコネクタ|18|DISPLAYコネクタ|
|19|HDMI Standard Aコネクタ|20|USB micro-Bコネクタ|USB2.0ホストコネクタ|
|21|USB Type A コネクタ|22|LANポート|
|23|DCジャック|24|内部配線用 DC12V 2PIN XHコネクタ|


### 1-1. microSDスロット
![1](/Image/Board_pic/cm3mb2_01.png)

Push-Push式 microSDスロット。<br>
※ComputeModule使用時のみシステムドライブとして使用可能。

### 1-2. CAMERAコネクタ
![2](/Image/Board_pic/cm3mb2_02.png)

Raspberry-pi標準のCAMERAモジュール接続用15pin FFCコネクタ。

### 1-3. シャットダウン LED
![3](/Image/Board_pic/cm3mb2_03.png)

緑点灯：シャットダウンプロセス実行中。

### 1-4. ステータス LED
![4](/Image/Board_pic/cm3mb2_04.png)

緑点滅：システムアクセス中。

### 1-5. 電源 LED
![5](/Image/Board_pic/cm3mb2_05.png)

緑点灯：電源ON。<br>
緑点滅(0.3秒間隔)：シャットダウン中。<br>
緑点滅(1.0秒間隔)：充電中(電源ON時)。<br>
赤点灯：バッテリー要充電。<br>
赤点滅(1.0秒間隔)：充電中(電源OFF時)。<br>

### 1-6. 内部配線用 LED接続7PIN ZHコネクタ
![6](/Image/Board_pic/cm3mb2_06.png)

1番 電源LEDの＋側<br>
2番 電源LEDの－側<br>
3番 Reserved<br>
4番 ステータスLEDの＋側<br>
5番 ステータスLEDの－側<br>
6番 シャットダウンLEDの＋側<br>
7番 シャットダウンLEDの－側<br>

### 1-7. USB Type A コネクタ
![7](/Image/Board_pic/cm3mb2_07.png)

USB2.0ホストコネクタ(1ポート)。

### 1-8. 電源 ON / OFF 用スイッチ
![8](/Image/Board_pic/cm3mb2_08.png)

### 1-9. 内部配線用 電源スイッチ接続 3PIN PHコネクタ
![9](/Image/Board_pic/cm3mb2_09.png)

1番 電源LED。<br>
2番 電源ボタン入力(押すとGNDと接続)。<br>
3番 電源GND。<br>

### 1-10. Li-ionバッテリー接続用 2PINコネクタ
![10](/Image/Board_pic/cm3mb2_10.png)

バックアップ用Li-ion電池から電源供給。

### 1-11. 200PIN DDR-SODIMM ソケット
![11](/Image/Board_pic/cm3mb2_11.png)

Raspberry Pi Compute Module 3/ 3 Lite 装着用ソケット。<br>
※RPi-CM3MB2にはCM3Liteが付属していません。<br>
※RPi-CM3MB2LにはCM3Liteが付属しています。(未装着)

### 1-12. 40PIN ピンヘッダー GPIOコネクタ
![12](/Image/Board_pic/cm3mb2_12.png)

40PIN GPIOのピン配列と説明<br>
※ 備考欄に記述のないピンの仕様については[Raspberry Pi公式ページ](https://pinout.xyz/#)をご参照ください。

| PIN# | 名称 | 備考 | PIN# | 名称 | 備考 |
|:---:|:---|:---|:---:|:---|:---|
|1|3.3V||2|5V||
|3|I2C SDA1/GPIO 2|I2Cアドレス 0x6F, 0x57 はRTCで予約済み |4|5V||
|5|I2C SCL1/GPIO 3|I2Cアドレス 0x6F, 0x57 はRTCで予約済み |6|GND||
|7|GPCLK/GPIO 4||8|UART TXD/GPIO 14||
|9|GND||10|UART RXD/GPIO 15||
|11|GPIO 17||12|PWM0/GPIO 18||
|13|GPIO 27||14|GND||
|15|GPIO 22||16|GPIO 23||
|17|3.3V||18|GPIO 24||
|19|SPI0 MOSI/GPIO 10||20|GND||
|21|SPI0 MISO/GPIO 9||22|GPIO 25||
|23|SPI0 SCLK/GPIO 11||24|SPI CE0/GPIO 8||
|25|GND||26|SPI CE1/GPIO 7||
|27|I2C SDA0/GPIO 0||28|I2C SCL0/GPIO 1||
|29|SHUTD_LED/GPIO 5|シャットダウンLED出力で予約済み|30|GND||
|31|SHUTD_BTN/GPIO 6|電源ボタン入力で予約済み|32|PWM0/GPIO 12||
|33|PWM1/GPIO 13||34|GND||
|35|SPI1 MISO/GPIO 19||36|STATUS_LED/GPIO 16|ステータスLED出力で予約済み|
|37|GPIO 26||38|SPI1 MOSI/GPIO 20||
|39|GND||40|SPI1 SCLK/GPIO 21||  

### 1-13. 12PIN ピンヘッダー 拡張GPIOコネクタ
![13](/Image/Board_pic/cm3mb2_13.png)

12PIN GPIO拡張コネクタのピン配列と説明

| PIN# | 名称 | 説明 | PIN# | 名称 | 説明 |
|:---:|:---|:---|:---:|:---|:---|
|1|SDA2/GPIO 28|I2C SDA2/GPIO 28|2|VBUS||
|3|SCL2/GPIO 29|I2C SCL2/GPIO 29|4|USBDM||
|5|GPIO 30|GPIO 30|6|USBDP||
|7|GPIO 31|GPIO 31|8|GND|GND|
|9|||10|||
|11|||12|||

### 1-14. メイン基板接続用コネクタ	
![14](/Image/Board_pic/cm3mb2_14.png)

拡張基板接続用コネクタ。

### 1-15. バックアップ電源用Li-ion電池ホルダー
![15](/Image/Board_pic/cm3mb2_15.png)

主電源切断時用 画面上の上側(＋)/下側(－)。<br>
※電池は出荷時に装着済み。

### 1-16. RTCバックアップ用 CR2032 電池ホルダー
![16](/Image/Board_pic/cm3mb2_16.png)

電池ホルダーに付属のCR2032を接続することで、RTCをバックアップ。

### 1-17. USB Bootモード設定用 3PINコネクタ
![17](/Image/Board_pic/cm3mb2_17.png)

USB micro-Bからのブートを有効にすることができます。<br>
1番-2番 ショート: 有効<br>
2番-3番 ショート: 無効<br>

### 1-18. DISPLAYコネクタ
![18](/Image/Board_pic/cm3mb2_18.png)

Raspberry-pi標準のタッチパネルディスプレイ接続用15pin FFCコネクタ。

### 1-19. HDMI Standard Aコネクタ
![19](/Image/Board_pic/cm3mb2_19.png)

HDMI Std. Aコネクタ。<br>
※Raspberry Piの仕様により最大1080p/60Hzまでとなります。

### 1-20. USB micro-Bコネクタ
![20](/Image/Board_pic/cm3mb2_20.png)

USB2.0ホストコネクタ。

### 1-21. USB Type A コネクタ
![21](/Image/Board_pic/cm3mb2_21.png)

USB2.0ホストコネクタ(2ポート)。

### 1-22. LANポート
![22](/Image/Board_pic/cm3mb2_22.png)

10/100BASE-TX対応 RJ45コネクタ。

### 1-23. DCジャック
![23](/Image/Board_pic/cm3mb2_23.png)

電源入力用ジャック(DC +12V/3A)。<br>
適合プラグ：外形φ5.5 内径φ2.1。<br>

### 1-24. 内部配線用 DC12V 2PIN XHコネクタ
![24](/Image/Board_pic/cm3mb2_24.png)

電源入力用コネクタ(DC +12V/3A)。<br>
1番 DC12V<br>
2番 GND<br>

