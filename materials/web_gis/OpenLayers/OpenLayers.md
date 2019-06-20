# OpenLayers入門
本教材は、QGISのプラグインであるQGIS2WEBを用いて、OpenLayers3でWEB地図を作成するための実習用教材です。以下の教材に従って、[完成例](https://yamauchi-inochu.github.io/ol3-test/index.html)のようなWEB地図が作成できれば実習完了です。この実習には、Atom等のテキストエディタが必要です。

本教材を使用する際は、[利用規約]をご確認いただき、これらの条件に同意された場合にのみご利用下さい。

[利用規約]:../../policy.md

**Menu**
------
* [OpenLayersとは？](#openlayersとは)
* [レイヤのスタイル調整とプラグインのインポート](#レイヤのスタイル調整とプラグインのインポート)
* [qgis2webを起動する](#qgis2leafを起動する)
* [index.htmlを編集する](#index.htmlを編集する)

**使用データ**

* [実習データ](https://raw.githubusercontent.com/gis-oer/datasets/master/vector/echizen.zip)
> [越前市オープンデータ] 越前市防災安全課　一次避難場所（風水害）、浸水想定区域（風水害）のデータを加工し、利用。

[越前市オープンデータ]:http://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html


---

## OpenLayersとは？
OpenLayersは、簡単にダイナミックなWEB地図を作ることができるオープンソースのJavaScriptライブラリです。Leafletと同様に、地図操作やベクトルレイヤ、タイルの読み込みなど様々な地図表現が可能です。OpenLayersに関する詳しい解説は、以下のリンクを参照してください。

> [OpenLayers公式](http://openlayers.org/)
> [wikipedia](https://ja.wikipedia.org/wiki/OpenLayers)
> [株式会社エヌ・シーエム OpenLayers](http://www.ncm-git.co.jp/pr/brain/experience/openlayers.html)

## レイヤのスタイル調整とプラグインのインポート
QGISに実習用データを読み込み、スタイルを調整する。次に、プラグインの管理とインストールから、「QGIS2WEB」を検索し、インストールする。
![QGISで調整](pic/leafpic_2.png)

[▲メニューへもどる]

## QGIS2webを起動する
`Web(W)>qgis2web`をクリックする。以下のような設定を行い、`Update preview`をした後、`Export`をクリックする。
![QGIS2Leaf](pic/leafpic_3.png)

①　レイヤをクリックしたときのポップアップの設定を行う。②　ズームレベルや計測機能などを設定する。ここで、ファイルの出力先を変更しておくと良い。　③　Basemapを選択する（複数選択は、 Ctrlキーを押しながら行う）

ローカルで、index.htmlファイルを開き中身を確認する。
![QGIS2Leaf](pic/leafpic_4.png)

[▲メニューへもどる]

## index.htmlを編集する
以下では、エクスポートしたindex.htmlを編集し、凡例の日本語化、Basemapの追加、レイヤの透過手法について解説しています。各機能の詳しい解説は、[完成例](https://yamauchi-inochu.github.io/ol3-test/index.html)のコードを参考にしてください。

### 凡例の変更(地図の切り替えウィンドウ)
layer.jsをテキストエディタで開き、//の個所を書き換える

```JavaScript
var lyr_flood_assumed_area = new ol.layer.Vector({
                source:jsonSource_flood_assumed_area,
                style: style_flood_assumed_area,
                title: "想定浸水区域"
            });var format_refugefirststage = new ol.format.GeoJSON();
var features_refugefirststage = format_refugefirststage.readFeatures(geojson_refugefirststage,
            {dataProjection: 'EPSG:4326', featureProjection: 'EPSG:3857'});
var jsonSource_refugefirststage = new ol.source.Vector();
jsonSource_refugefirststage.addFeatures(features_refugefirststage);var lyr_refugefirststage = new ol.layer.Vector({
                source:jsonSource_refugefirststage,
                style: style_refugefirststage,
                title: "一次避難所"
            });
```

### ポップアップの編集
layersフォルダにあるlayers.jsを開き、テキストエディタの置換機能を用いて、フィールド名を日本語にする。`no label`を `inline label`に書き換える。

```JavaScript
lyr_flood_assumed_area.set('fieldLabels', {'SAUID': 'inline label', 'SAUPDATE': 'inline label', 'SAFIELD000': 'inline label', 'SAFIELD001': 'inline label', });
lyr_refugefirststage.set('fieldLabels', {'SAFIELD003': 'inline label', 'SAFIELD004': 'inline label', 'SAFIELD005': 'inline label', 'SAFIELD006': 'inline label', 'test': 'inline label', });
```


### ベースマップの追加
var baseLayerに地理院地図を追加する。

```JavaScript
var baseLayer = new ol.layer.Group({
    'title': 'Base maps',
    layers: [

  new ol.layer.Tile({
      'title': 'OSM',
      'type': 'base',
      source: new ol.source.OSM()
  }),
  new ol.layer.Tile({
      'title': 'Stamen Terrain',
      'type': 'base',
      source: new ol.source.Stamen({
          layer: 'terrain'
      })
  }),//以下を追加

  new ol.layer.Tile({
    'title': '地理院地図',
    'type': 'base',
              source: new ol.source.XYZ({
                attributions: [attribution],
                url: 'http://cyberjapandata.gsi.go.jp/xyz/std/{z}/{x}/{y}.png'
              })
            })
  ]
});
```

### ポリゴンを透過する
stylesフォルダのflood_assumed_area_style.jsを開き、透過‘1.0’を0.7に変更する。

```JavaScript
var size = 0;function categories_flood_assumed_area(feature, value) {
                 switch(value) {case "0.0-0.5":
	return [ new ol.style.Style({
         fill: new ol.style.Fill({color: ‘rgba(161,231,253,0.7)’}) //1.0から0.7にする
    })];  //以下、省略

```

### 表示の確認
index.htmlをブラウザで開き、編集内容を確認する。
![QGIS2Leaf](pic/leafpic_10.png)

[▲メニューへもどる]

#### ライセンスに関する注意事項
本教材で利用しているキャプチャ画像の出典やクレジットについては、[その他のライセンスについて]よりご確認ください。

[利用規約]:../../../policy.md
[その他のライセンスについて]:../../lisence.md
[▲メニューへもどる]:./OpenLayers.md#Menu
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
