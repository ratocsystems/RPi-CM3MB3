## Raspberry Pi用OS Raspbianのインストール

1) Class10のmicroSD(8～32G)を用意します。  
*64GB以上のSDカードの場合、exFATでフォーマットされます。
RaspbianはexFATに対応していませんので、別のツールを使ってFAT16またはFAT32でフォーマットする必要があります。*

2) SDカード用フォーマッターとユーザーマニュアルをダウンロードします。  
SDアソシエーションのダウンロードページから'SDメモリカードフォーマッター'と'ユーザーマニュアル'をダウンロードします。
https://www.sdcard.org/jp/downloads/formatter_4/index.html

3) 'SDメモリカードフォーマッター'を使って、SDカードをフォーマットします。
ファーマット方法につきましては、ダウンロードしたユーザーマニュアルをご参照ください。

4) Raspberry財団公式ホームページで
https://www.raspberrypi.org/downloads/raspbian/  
「RASPBIAN STRETCH WITH DESKTOP」 のZIPファイルをPCでダウンロードします。

5) ETCHERツールを使用して、ダウンロードしたZIPイメージファイルをmicroSDカードへ書き込みます。  
ETCHERツールはこちらよりダウンロードします。  
https://etcher.io/  

「Select image」をクリックします。  

![Etcher01](/Image/Raspbian_pic/Etcher_01.png)  

ダウンロードしたzipファイルを選択し「開く」をクリックします。

![Etcher02](/Image/Raspbian_pic/Etcher_02.png)  

「Flash!」をクリックします。  

![Etcher03](/Image/Raspbian_pic/Etcher_03.png)  

「Flash Complete!」が表示されると書き込み完了です。  

![Etcher04](/Image/Raspbian_pic/Etcher_04.png)
