# GRASSビギナーズマニュアル
　本教材は、GRASS GISの入門者向け実習用教材です。GRASS GIS（7系）の機能やデータの読み込みなどについて解説しています。

　課題形式で使用する場合は、本教材を一読した後、課題ページへお進みください。GIS初学者は、本教材を進める前に[GISの基本概念]の教材を確認しておいてください。本教材を使用する際は、[利用規約]をご確認いただき、これらの条件に同意された場合にのみご利用下さい。

**Menu**
----------
* [GRASS GISとは？](#grass_gisとは？)
* [インストール](#インストール)
* [ファイル形式について](#ファイル形式について)
* [GRASSの起動](#grassの起動)
* [機能説明](#機能説明)
* [マップセットにラスタデータを読み込む](#マップセットにラスタデータを読み込む)
* [コマンドコンソールとモジュールツリー](#コマンドコンソールとモジュールツリー)
* [レイヤの色分け](#レイヤの色分け)
* [レイアウト](#レイアウト)
* [参考ページの紹介](#参考ページの紹介)

**実習用データ**

実習をはじめる前に、[tokyo]をダウンロードしてください。

**スライド教材**

本教材は、[スライド_GRASSビギナーズマニュアル]としても、ご利用いただけます。

[tokyo]:https://github.com/gis-oer/datasets/raw/master/tokyo.zip

----------

## GRASS_GISとは？
　GRASS GISは、無償で利用できるオープンソースGISです。ラスタデータやベクタデータに関連する処理の機能が充実しており、地形解析や画像分類等で活用されています。本教材で主として利用しているQGISのツールボックスから、GRASS GISの機能を呼び出すこともできます。以下では、GRASS GISの入門として、基本機能と地図の作成手法について解説しています。GRASS GISの実践的な利用法について知りたい方は、[ラスタデータの分析]の教材等を参照してください。  

 [▲メニューへもどる]  

## インストール
　[GRASS GISの公式ページ] にアクセスして、GRASS GISをダウンロードする。解凍したファイルのガイドに従ってインストールを行う。

![インストール](pic/grasspic_1.png)

[GRASS GISの公式ページ]:https://grass.osgeo.org/

[▲メニューへもどる]

## ファイル形式について

![ファイル形式](pic/grasspic_2.png)

[▲メニューへもどる]

## GRASSの起動
GRASS GISをインストールした後、デスクトップのアイコンをダブルクリックし、GRASS GISを起動する。
![起動する](pic/grasspic_3.png)

[▲メニューへもどる]

### ロケーションとマップセットの作成
`Select GRASS Location>New`を選択し、データベースとロケーション名の設定から、プロジェクトロケーションとロケーションタイトルを入力する。`Create user mapset`にチェックをつけ、`次へ`をクリックする。
![ロケーションとマップセット](pic/grasspic_4.png)

`EPSGコードを指定`にチェックをつけ、`次へ`をクリックする。
![ロケーションとマップセット](pic/grasspic_5.png)

EPSGコードを`6667`とし、`次へ`をクリックする。
![ロケーションとマップセット](pic/grasspic_6.png)

以下のように、新規ロケーションが出力される。
![ロケーションとマップセット](pic/grasspic_7.png)

ロケーションを作成すると、マップセットのウィンドウが表示されるため、新規マップセットの名前を入力し、`OK`をクリックする。ウィンドウが表示されない場合は、`Select GRASS Mapset＞New`をクリックする。
![ロケーションとマップセット](pic/grasspic_8.png)

[▲メニューへもどる]

### マップセットを表示する

`Select GRASS Location`で先ほど出力したロケーションを選択し、`Select GRASS Mapset`で先ほどのマップセットを選択し、`Start GRASS session`を実行する。
![ロケーションとマップセット](pic/grasspic_9.png)

[▲メニューへもどる]

## 画面説明
GRASS GISを起動すると、以下のような画面が表示される。
![画面説明](pic/grasspic_10.png)

[▲メニューへもどる]

## 機能説明
　GRASS GISには、QGISのように地図の表示、データ作成、分析等の機能が搭載されています。以下では、それらの機能について簡単に解説しています。
![機能説明](pic/grasspic_11.png)
1. 新規マップ表示　
2. 新規ワークスペース作成　
3. ワークスペースの読み込みと書き出し
4. マップセット内のデータ読み込み（④の右側のボタンは読み込むデータの形式によって選択する）
5. データの編集　
6. 属性テーブルの表示　
7. データのインポート　
8. ラスタ計算機　
9. 幾何補正

各メニューの内容は以下のとおりである。
![機能説明](pic/grasspic_12.png)

![機能説明](pic/grasspic_13.png)

![機能説明](pic/grasspic_14.png)

[▲メニューへもどる]

## コマンドコンソールとモジュールツリー

　GRASS GISでは、コマンドコンソールやそれをツリー上にまとめたモジュールツリーから処理が実行できます。上記の利用例は、[ラスタデータの分析]や[ネットワーク分析]の教材で詳しく解説しているため、こちらでは説明していません。
　![コマンドコンソールとモジュールツリー](pic/grasspic_15.png)

- レイヤー:レイヤを表示。
- コンソール:コマンドを入力し、処理を実行。
- モジュール：ツリーから選択し、処理を実行。

[▲メニューへもどる]

## マップセットにラスタデータを読み込む
　以下では、マップセットにデータを読み込む手法について解説しています。下の図の赤枠のアイコンをクリックし、`ラスターデータのインポート`から、作成したマップセットのロケーションと対応するラスタを選択し、`インポート`をクリックし読み込む。
![マップセット](pic/grasspic_16.png)

以下のように、ラスタデータが表示される。
![マップセット](pic/grasspic_17.png)

[▲メニューへもどる]

### レイヤの色分け
ラスタの値（ここでは標高値）に応じた色分けは、`ラスター＞カラー調整＞Manage color rules Interactively`から行う。ここでは、例として、以下のように分類数と値を入力する。
![色分け](pic/grasspic_18.png)
1. 分類数を5とする。
2. 分類値と色を調整する。
3. `OK`をクリックする。

以下のように、ラスタデータの配色が調整できた。
![色分け](pic/grasspic_19.png)

[▲メニューへもどる]

## レイアウト
　以下では、GRASS GISでのマップのレイアウトについて解説しています。地図のレイアウトは、`ファイル＞カートグラフィックコンポーザー`から実行する。
![レイアウトa](pic/grasspic_20.png)

`カートグラフィックコンポーザー`を起動し、以下の手順で、地図や凡例などを挿入する。
![レイアウトb](pic/grasspic_21.png)
1. 地図の範囲を選択する（一番最初に設定する）。
2. ラスタマップを追加する。
3. ベクタマップを追加する。
4. 凡例、方位、縮尺を追加する。
5. 地図の書き出し（PDF）をする。

地図の範囲をドラッグして設定し、ラスタマップを追加する。
![レイアウトc](pic/grasspic_22.png)

以下のアイコンをクリックし、地図の凡例を追加する。
![レイアウトd](pic/grasspic_23.png)

以下のアイコンをクリックし、地図の縮尺と方位を追加する。※バージョンによって、方位記号が追加できない場合があるようです。
![レイアウトe](pic/grasspic_24.png)

縮尺は、長さを設定し、単位を選択する（今回はデフォルトを使用）。縮尺バーのデザインを選択し、`OK`をクリックする。追加されたら、追加アイテムの配置を変更する。方位記号は、デザインを選択し、スタイルでサイズを整え`OK`をクリックする。それぞれ追加できたら、地図に追加したアイテムの配置を調整する。


配置が完了したら、PDFで書き出す（プレビューは、表示されない場合がある）。
![レイアウトh](pic/grasspic_25.png)

[▲メニューへもどる]

## 参考ページの紹介
1. [GRASS GISの公式ページ]
2. [FOSS4G を活用した衛星データの利用のためのオープン・リソースの構築]

[FOSS4G を活用した衛星データの利用のためのオープン・リソースの構築]:http://foss4g.kii.gscc.osaka-cu.ac.jp/moodle/

[▲メニューへもどる]

#### この教材の[課題ページ_GRASS]へ進む

#### ライセンスに関する注意事項
本教材で利用しているキャプチャ画像の出典やクレジットについては、[その他のライセンスについて]よりご確認ください。

[▲メニューへもどる]:./GRASS.md#Menu
[利用規約]:../../policy.md
[その他のライセンスについて]:../license.md
[よくある質問とエラー]:../questions/questions.md

[GISの基本概念]:../00/00.md
[QGISビギナーズマニュアル]:../QGIS/QGIS.md
[GRASSビギナーズマニュアル]:../GRASS/GRASS.md
[リモートセンシングとその解析]:../06/06.md
[既存データの地図データと属性データ]:../07/07.md
[空間データ]:../08/08.md
[空間データベース]:../09/09.md
[空間データの統合・修正]:../10/10.md
[基本的な空間解析]:../11/11.md
[ネットワーク分析]:../12/12.md
[領域分析]:../13/13.md
[点データの分析]:../14/14.md
[ラスタデータの分析]:../15/15.md
[傾向面分析]:../16/16.md
[空間的自己相関]:../17/17.md
[空間補間]:../18/18.md
[空間相関分析]:../19/19.md
[空間分析におけるスケール]:../20/20.md
[視覚的伝達]:../21/21.md
[参加型GISと社会貢献]:../26/26.md

[地理院地図]:https://maps.gsi.go.jp
[e-Stat]:https://www.e-stat.go.jp/
[国土数値情報]:http://nlftp.mlit.go.jp/ksj/
[基盤地図情報]:http://www.gsi.go.jp/kiban/
[地理院タイル]:http://maps.gsi.go.jp/development/ichiran.html


[スライド_GISの基本概念]:https://github.com/gis-oer/gis-oer/raw/master/materials/00/00.pptx
[スライド_QGISビギナーズマニュアル]:https://github.com/gis-oer/gis-oer/raw/master/materials/QGIS/QGIS.pptx
[スライド_GRASSビギナーズマニュアル]:https://github.com/gis-oer/gis-oer/raw/master/materials/GRASS/GRASS.pptx
[スライド_リモートセンシングとその解析]:https://github.com/gis-oer/gis-oer/raw/master/materials/06/06.pptx
[スライド_既存データの地図データと属性データ]:https://github.com/gis-oer/gis-oer/raw/master/materials/07/07.pptx
[スライド_空間データ]:https://github.com/gis-oer/gis-oer/raw/master/materials/08/08.pptx
[スライド_空間データベース]:https://github.com/gis-oer/gis-oer/raw/master/materials/09/09.pptx
[スライド_空間データの統合・修正]:https://github.com/gis-oer/gis-oer/raw/master/materials/10/10.pptx
[スライド_基本的な空間解析]:https://github.com/gis-oer/gis-oer/raw/master/materials/11/11.pptx
[スライド_ネットワーク分析]:https://github.com/gis-oer/gis-oer/raw/master/materials/12/12.pptx
[スライド_領域分析]:https://github.com/gis-oer/gis-oer/raw/master/materials/13/13.pptx
[スライド_点データの分析]:https://github.com/gis-oer/gis-oer/raw/master/materials/14/14.pptx
[スライド_ラスタデータの分析]:https://github.com/gis-oer/gis-oer/raw/master/materials/15/15.pptx
[スライド_空間補間]:https://github.com/gis-oer/gis-oer/raw/master/materials/18/18.pptx
[スライド_視覚的伝達]:https://github.com/gis-oer/gis-oer/raw/master/materials/21/21.pptx
[スライド_参加型GISと社会貢献]:https://github.com/gis-oer/gis-oer/raw/master/materials/26/26.pptx

[課題ページ_QGISビギナーズマニュアル]:../tasks/t_qgis_entry.md
[課題ページ_GRASSビギナーズマニュアル]:../tasks/t_grass_entry.md
[課題ページ_リモートセンシングとその解析]:../tasks/t_06.md
[課題ページ_既存データの地図データと属性データ]:../tasks/t_07.md
[課題ページ_空間データ]:../tasks/t_08.md
[課題ページ_空間データベース]:../tasks/t_09.md
[課題ページ_空間データの統合・修正]:../tasks/t_10.md
[課題ページ_基本的な空間解析]:../tasks/t_11.md
[課題ページ_ネットワーク分析]:../tasks/t_12.md
[課題ページ_基本的な空間解析]:../tasks/t_13.md
[課題ページ_点データの分析]:../tasks/t_14.md
[課題ページ_ラスタデータの分析]:../tasks/t_15.md
[課題ページ_空間補間]:../tasks/t_18.md
[課題ページ_視覚的伝達]:../tasks/t_21.md
[課題ページ_参加型GISと社会貢献]:../tasks/t_26.md
<h2 style="background-color:#F8F5FD;text-align:center;">教材の利用に関するアンケート</h2>　本プロジェクトでは、教材の改良を目的とした任意アンケートを実施しています。ご協力いただける方は、<a href="https://customform.jp/form/input/14328/">アンケート</a>にお進みください。ご協力のほどよろしくお願いいたします。<br><br>※ 本アンケートの成果は、教材の改良のほか、学会での発表等の研究目的でも利用します。また、本アンケートでは、個人が特定できるような質問は設けておりません。
