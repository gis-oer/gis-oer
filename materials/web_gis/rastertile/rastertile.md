# タイル地図入門（ラスタ）
　本教材は、QGISを利用したラスタタイルの作成とLeafletでの表示手法について解説しています。以下の教材に従って、[完成例](https://yamauchi-inochu.github.io/tile-test/index.html)のようなWEB地図が作成できれば実習完了です。GitHub等の操作法や基本的なプログラミングについての解説はしていません。Leafletの利用法についての解説は、Leafletの教材を参照ください。

本教材を使用する際は、[利用規約]をご確認いただき、これらの条件に同意された場合にのみご利用下さい。

**Menu**
------
* [タイル地図とは](#タイル地図とは)
* [タイルの作成](#タイルの作成)
* [Leafletで表示](#Leafletで表示)

**使用データ**

* [サンプル画像]

## タイル地図（ラスタ）とは
- 極地の一部を除き、世界を正方形タイル(一般的には、256×256のピクセル画像)として分割したもの（メルカトル投影）
- TMSやWMTS(両者は原点が異なる)の形式で配信され、スクロールやズーミングの操作に応じてタイルを表示するもの
- /{z}/{x}/{y}.{ext}で容易にアクセスできる

> 各項目について、以下のようなサイトが詳しいです。
> [OSM wiki JA:タイル](https://wiki.openstreetmap.org/wiki/JA:%E3%82%BF%E3%82%A4%E3%83%AB)
> [国土地理院 ズームレベル・タイル座標](https://maps.gsi.go.jp/development/siyou.html)


## タイルの作成
以下では、QGISを利用しタイル地図（TMS形式）を作成する手法について解説しています。

![ratertile](./pic/rastertile_pic1.png)

1. QGISを起動し、タイル化したい位置情報つきのラスタデータ（EPSG:3857）を用意する。ない場合は、[サンプル画像]を利用する。
2. プラグインの管理とインストールから、QTilesをインストールする。
3. プラグイン＞ QTiles＞ QTilesを起動し、出力ファイルを設定する。
4. 出力場所、出力するレイヤ、ズーミング（ここでは17-22とした）、パラメーター（Background transparsityを0とし、Use TMS tiles convention(Slippy Map by default)とrender tiles outside of layers extents(with in extent) ）を指定し、OKをクリックする。
5. OKをクリックすると.zip形式のファイルが出力される。解凍するとズームレベルごとに画像が入ったフォルダが作成されている。

[▲メニューへもどる]

## Leafletで表示
以下では、Leafletを利用し出力したラスタタイルを表示する手法について解説しています。最初に、[Leaflet](https://leafletjs.com/)をダウンロードしてください。ダウンロード後に、出力したタイルのファイル（解凍済み）をLeafletのフォルダに移動し、下記のようなhtmlを作成する。

```html
<body>

	<div id="map0" style="width: 800px; height: 600px;"></div>

	<script>
		var map1 = L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/ort/{z}/{x}/{y}.jpg', {
		maxZoom: 18,
		attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
		});

		var layer1 = L.tileLayer('./tile/{z}/{x}/{y}.png', {
		tms:true,
		minZoom: 18,
		maxZoom: 22,
		attribution: ""
		});

		var map2 = L.tileLayer('https://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png', {
		maxZoom: 18,
		attribution: "<a href='https://maps.gsi.go.jp/development/ichiran.html' target='_blank'>地理院タイル</a>"
		});

		var map = L.map('map0',{
			center:[34.9558,139.8139],
			zoom:18,
			layers:[map1,layer1]
		});

		var basemaps = {
		"GSI ort":map1,
		"GSI std":map2
		};

		var layers= {
		"phot": layer1
		};

		L.control.layers(basemaps,layers).addTo(map);

		L.control.scale({imperial: false}).addTo(map);

	</script>

</body>

```

index.htmlを開くと出力したタイル地図と地理院タイルを重ねて表示することができる。

[▲メニューへもどる]


#### ライセンスに関する注意事項
本教材で利用しているキャプチャ画像の出典やクレジットについては、[その他のライセンスについて]よりご確認ください。

[その他のライセンスについて]:../../license.md
[サンプル画像]:https://github.com/gis-oer/datasets/raw/master/raster/sunayama.tif
[▲メニューへもどる]:./rastertile.md#Menu
[利用規約]:../../../policy.md
[利用規約]:../../../policy.md
[その他のライセンスについて]:../../license.md
[よくある質問とエラー]:../../questions/questions.md

[GISの基本概念]:../../00/00.md
[QGISビギナーズマニュアル]:../../QGIS/QGIS.md
[GRASSビギナーズマニュアル]:../../GRASS/GRASS.md
[リモートセンシングとその解析]:../../06/06.md
[既存データの地図データと属性データ]:../../07/07.md
[空間データ]:../../08/08.md
[空間データベース]:../../09/09.md
[空間データの統合・修正]:../../10/10.md
[基本的な空間解析]:../../11/11.md
[ネットワーク分析]:../../12/12.md
[領域分析]:../../13/13.md
[点データの分析]:../../14/14.md
[ラスタデータの分析]:../../15/15.md
[傾向面分析]:../../16/16.md
[空間的自己相関]:../../17/17.md
[空間補間]:../../18/18.md
[空間相関分析]:../../19/19.md
[空間分析におけるスケール]:../../20/20.md
[視覚的伝達]:../../21/21.md
[参加型GISと社会貢献]:../../26/26.md

[地理院地図]:https://maps.gsi.go.jp
[e-Stat]:https://www.e-stat.go.jp/
[国土数値情報]:http://nlftp.mlit.go.jp/ksj/
[基盤地図情報]:http://www.gsi.go.jp/kiban/
[地理院タイル]:http://maps.gsi.go.jp/development/ichiran.html

[課題ページ_QGISビギナーズマニュアル]:../../tasks/t_qgis_entry.md
[課題ページ_GRASSビギナーズマニュアル]:../../tasks/t_grass_entry.md
[課題ページ_リモートセンシングとその解析]:../../tasks/t_06.md
[課題ページ_既存データの地図データと属性データ]:../../tasks/t_07.md
[課題ページ_空間データ]:../../tasks/t_08.md
[課題ページ_空間データベース]:../../tasks/t_09.md
[課題ページ_空間データの統合・修正]:../../tasks/t_10.md
[課題ページ_基本的な空間解析]:../../tasks/t_11.md
[課題ページ_ネットワーク分析]:../../tasks/t_12.md
[課題ページ_基本的な空間解析]:../../tasks/t_13.md
[課題ページ_点データの分析]:../../tasks/t_14.md
[課題ページ_ラスタデータの分析]:../../tasks/t_15.md
[課題ページ_空間補間]:../../tasks/t_18.md
[課題ページ_視覚的伝達]:../../tasks/t_21.md
[課題ページ_参加型GISと社会貢献]:../../tasks/t_26.md
