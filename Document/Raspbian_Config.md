## Raspberry Piの基本設定  
ここでは以下機能の設定方法について説明しています。  
本製品をHDMIケーブルでディスプレイと接続して起動してください。  
※ OSはRaspbian Stretch（2017年12月）を使用して説明しています。

1) ローカライゼーションの設定  
2) RTCとLEDの設定
3) シャットダウンスクリプトの登録 

### 1. ローカライゼーションの設定  
「言語」「タイムゾーン」「キーボード」を日本設定に変更します。  

[Preferences]-[Raspberry Pi Configuration]を選択します。

![Local_01](/Image/Raspbian_pic/Local_01.png)

[Localisation]を選択します。

![Local_02](/Image/Raspbian_pic/Local_02.png)

「Set Locale」をクリックします。

![Local_03_00](/Image/Raspbian_pic/Local_03_00.png)

Language: ja(Japanese)  
Country： JP(Japan)  
Character Set：UTF-8  
を選択し「OK」をクリックします。

![Local_03](/Image/Raspbian_pic/Local_03.png)

「Set Timezone」をクリックします。

![Local_04_00](/Image/Raspbian_pic/Local_04_00.png)

Area： Japan  
を選択し「OK」をクリックします。

![Local_04](/Image/Raspbian_pic/Local_04.png)

「Set Keyboard」をクリックします。

![Local_05_00](/Image/Raspbian_pic/Local_05_00.png)

Country: Japan  
Variant: Japanese(OADG 109A)  
を選択し「OK」をクリックします。

![Local_05](/Image/Raspbian_pic/Local_05.png)

最後に「OK」をクリックします。

![Local_07_00](/Image/Raspbian_pic/Local_07_00.png)

設定を有効にするには「Yes」をクリックします。

![Local_07](/Image/Raspbian_pic/Local_07.png)

  
### 2. RTCとLEDの設定  
「Real Time Clock」と「アクセス・シャットダウン時のLED動作」を有効にします。

#### (2-1) RTCとLEDの設定  

[設定]-[Rapberry Piの設定]をクリックします。  

![RTC_01](/Image/RTC_LED_pic/RTC_01.png)

[インターフェース]で"I2C"を有効にし、OSを再起動します。

![RTC_02](/Image/RTC_LED_pic/RTC_02.png)

ターミナルを起動します。

![RTC_03](/Image/RTC_LED_pic/RTC_03.png)

sudo nano /boot/config.txt と入力しファイルを編集します。

![RTC_04](/Image/RTC_LED_pic/RTC_04.png)

以下の3行を追記し、キーボードの[Ctrl+O]を押します。

dtoverlay=pi3-act-led,gpio=16  
dtoverlay=gpio-poweroff,gpiopin=5  
dtoverlay=i2c-rtc,mcp7941x  

![RTC_05](/Image/RTC_LED_pic/RTC_05.png)

エンターキーで上書きします。  

![RTC_06](/Image/RTC_LED_pic/RTC_06.png)

sudo nano /lib/udev/hwclock-set と入力しファイルを編集します。

![RTC_07](/Image/RTC_LED_pic/RTC_07.png)

以下の３行をコメントアウト(各行の先頭に#を追記)し  
キーボードの[Ctrl+O]を押します。

#if [ -e /run/systemd/system ] ; then  
#exit 0  
#fi  

![RTC_08](/Image/RTC_LED_pic/RTC_08.png)

エンターキーで上書きします。  

![RTC_09](/Image/RTC_LED_pic/RTC_09.png)


#### (2-2) RTCの動作確認  

ターミナル上でhwclockコマンドを使用して動作確認を行うことができます。  
"sudo hwclock -r" :RTCの時刻読み出し  
"sudo hwclock -w" :システムの時間をRTCへ書き込む  
"sudo hwclock -s" :RTCの時間をシステムへ書き込む(スタートアップ時に実行される)  
"sudo hwclock -c" :RTCから10秒間隔で時刻読み出し(Ctrl+Cで停止)

![RTC_10](/Image/RTC_LED_pic/RTC_10.png)


#### (2-3) LEDの動作確認  

[アクセスLEDの動作確認]  
ファイルアクセスすると、アクセスLEDが点滅します。

[シャットダウンLEDの動作確認]  
OSシャットダウン時にシャットダウンLEDが点灯し、電源LEDが14秒間点滅後に電源OFFとなります。  

### 3. シャットダウンスクリプトの登録  

電源ボタンの長押し(3秒以上)で、システムのシャットダウンを行えるようになるPythonスクリプトを登録します。  

#### (3-1) スクリプトファイルのダウンロードと有効化  

ターミナルを起動します。

![SDWN_01](/Image/SDWN_pic/SDWN_01.png)

プログラムを保存するディレクトリーを作成し移動します。(例ではratocを作成)  
mkdir ratoc  
cd ratoc  

![SDWN_02](/Image/SDWN_pic/SDWN_02.png)

スクリプトファイル"shutd_btn.py"をGitHubからダウンロードします。  
sudo wget https://github.com/ratocsystems/rpi-cm3/raw/master/shutdown/shutd_btn.py

![SDWN_03](/Image/SDWN_pic/SDWN_03.png)

スクリプトファイルを実行可能にします。  
sudo chmod 755 ~/ratoc/shutd_btn.py

![SDWN_04](/Image/SDWN_pic/SDWN_04.png)

#### (3-2) サービスファイルのダウンロードと開始  

サービスファイル"shutd_btn.service"をGitHubからダウンロードします。  
sudo wget https://github.com/ratocsystems/rpi-cm3/raw/master/shutdown/shutd_btn.service"

![SDWN_05](/Image/SDWN_pic/SDWN_05.png)

サービスを/etc/systemd/systemへコピーします。  
sudo cp shutd_btn.service /etc/systemd/system/shutd_btn.service

![SDWN_06](/Image/SDWN_pic/SDWN_06.png)

サービスを開始します。  
sudo systemctl start shutd_btn.service

![SDWN_07](/Image/SDWN_pic/SDWN_07.png)

システム起動時にサービスが自動で実行されるように設定します。  
sudo systemctl enable shutd_btn.service  

sudo systemctl disable shutd_btn.service  
で自動での実行が無効となります。

![SDWN_08](/Image/SDWN_pic/SDWN_08.png)

サービスが実行されているかを確認します。  
sudo systemctl status shutd_btn.service

以下の表示となっていれば正常に実行されています。

![SDWN_09](/Image/SDWN_pic/SDWN_09.png)

