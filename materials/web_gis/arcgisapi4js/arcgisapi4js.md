# ArcGIS API for JavaScript入門(作成中)
本教材は、[ArcGIS API for JavaScript](https://www.esrij.com/products/arcgis-api-for-javascript/)を用いて空間データをインターネットで公開する手法について解説しています。以下の教材を参考に[完成例](https://yamauchi-inochu.github.io/arcgis_api/sample.html)のような地図が作成できれば実習完了となります。この実習では、作成した地図の公開にGitHubのgh-pagesの機能を利用します。

本教材を使用する際は、[利用規約]をご確認いただき、これらの条件に同意された場合にのみご利用下さい。

**Menu**
------
* [ArcGIS API for JavaScriptとは？](#arcgis_api_for_javascriptとは？)
* [地図を作成する](#地図を作成する)


**使用データ**

* [越前市想定浸水区域](https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/flood_assumed_area.kml)

* [越前市避難所](https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/refuge.kml)

> [越前市オープンデータ] 越前市防災安全課　一次避難場所（風水害）、浸水想定区域（風水害）のデータを加工し、利用。

[越前市オープンデータ]:http://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html

--------

## ArcGIS_API_for_JavaScriptとは？
　ArcGIS API for JavaScriptとは、ESRI社が開発者向けに、ArcGISの機能をJavaScriptで利用できるように提供するものである。ArcGIS API for JavaScriptの詳細は、[ESRIジャパンのArcGIS API for JavaScript ](https://www.esrij.com/products/arcgis-api-for-javascript/)のページを参照してください。

[▲メニューへもどる]

## 地図を作成する
　以下では、ArcGIS API for JavaScriptを用いて、データを表示する方法や縮尺等のアイテムを表示する手法について解説します。解説は以下のコード内のテキストを参照してください。

 > 以下のコードは、初心者用にArcGIS API for JavaScriptの使い方をくわしく解説した[EsriJapan GitHub はじめての Web マッピングアプリケーション開発：地図表示編](https://community.esri.com/docs/DOC-11394)や[EsriJapanのGitHub :arcgis-samples-4.0-js]を(https://github.com/EsriJapan/arcgis-samples-4.0-js)を参考に作成しています。

### ベースマップを作成する
ArcGIS API for JavaScriptの機能を呼び出すため、以下の2行を<head>内に追加したHTMLを作成してください。

- `<link rel="stylesheet" href="https://js.arcgis.com/4.7/esri/css/main.css">`
- `<script src="https://js.arcgis.com/4.7/"></script>`

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
  <title>test</title>

  <style>
    html,
    body,
    #viewDiv {
      padding: 0;
      margin: 0;
      height: 100%;
      width: 100%;
    }
    #layerToggle {
      bottom: 60px;
      right: 10px;
      position: absolute;
      z-index: 99;
      background-color: white;
      border-radius: 8px;
      padding: 10px;
      opacity: 0.75;
    }
  </style>

  <link rel="stylesheet" href="https://js.arcgis.com/4.7/esri/css/main.css">
  <script src="https://js.arcgis.com/4.7/"></script>

  <script>
  　//機能の呼び出し
    require([
      "esri/Map",
      "esri/views/MapView",
      "dojo/domReady!"

    ], function(
      Map,
      MapView,
    ) {
      //ベース地図の呼び出し
      const map = new Map({
        basemap: "streets"
      });
      //表示範囲の指定
      const view = new MapView({
        container: "viewDiv",
        map: map,
        center: [136.570, 36.479],
        zoom: 11
      });
});
  </script>

</head>

<body>
  <div id="viewDiv"></div>
</body>

</html>
```
### 表示位置を越前市周辺に変更する

```JavaScript

const view = new MapView({
  container: "viewDiv",
  map: map,
  center: [136.1688, 35.9032],
  zoom: 11
});

```

### スケールを追加する

```JavaScript
　//requireに"esri/widgets/ScaleBar"を追加し、fuctionにScaleBarを追加する
  require([
    "esri/Map",
    "esri/views/MapView",
    "esri/widgets/ScaleBar"
    "dojo/domReady!",

  ], function(
    Map,
    MapView,
    ScaleBar
  ) {
    const map = new Map({
      basemap: "streets"
    });

    const view = new MapView({
      container: "viewDiv",
      map: map,
      center: [136.1688, 35.9032],
      zoom: 11
    });

  //スケールの追加
  const scalebar = new ScaleBar({
    view: view,
    unit: "dual"
  });

  //スケールバーの設定
  view.ui.add(scalebar, "bottom-left");

});

```

### 方位を追加する

```JavaScript
//requireに"esri/widgets/ScaleBar"を追加し、fuctionにScaleBarを追加する

require([
  "esri/Map",
  "esri/views/MapView",
  "esri/widgets/ScaleBar",
  "esri/widgets/Compass",
  "dojo/domReady!"

], function(
  Map,
  MapView,
  ScaleBar,
  Compass
) {
  const map = new Map({
    basemap: "streets"
  });

  const view = new MapView({
    container: "viewDiv",
    map: map,
    center: [136.1688, 35.9032],
    zoom: 11
  });

const scalebar = new ScaleBar({
  view: view,
  unit: "dual"
});

view.ui.add(scalebar, "bottom-left");

const compass = new Compass({
  view: view,
});

view.ui.add(compass, "up-left");

});

```

### レイヤを追加する
ここでは表示例用レイヤとして、事前に作成しGitHubで公開している以下のKMLファイルを読み込みます。

- https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/flood_assumed_area.kml
- https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/refuge.kml

```JavaScript
//requireに"esri/layers/KMLLayer"を追加し、fuctionにKMLLayer"を追加する

require([
  "esri/Map",
  "esri/views/MapView",
  "esri/widgets/ScaleBar",
  "esri/widgets/Compass",
  "esri/layers/KMLLayer",

  "dojo/domReady!"

], function(
  Map,
  MapView,
  ScaleBar,
  Compass,
  KMLLayer
) {

  //KMLを追加する
  const area = new KMLLayer({
        url:"https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/flood_assumed_area.kml",
        id:"area"
      });
  //KMLを追加する
  const refuge = new KMLLayer({
        url:"https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/refuge.kml",
        id:"refuge"
          });
  //KMLを指定する
  const map = new Map({
    basemap: "streets",
    layers: [area,refuge]

  });

  const view = new MapView({
    container: "viewDiv",
    map: map,
    center: [136.1688, 35.9032],
    zoom: 11
  });

const scalebar = new ScaleBar({
  view: view,
  unit: "dual"
});

view.ui.add(scalebar, "bottom-left");

const compass = new Compass({
  view: view,
});

view.ui.add(compass, "up-left");

});

```

### レイヤの選択機能を追加する
<body>内に以下を記述する

```html
<div id="viewDiv"></div>
<span id="layerToggle">
  <h2>レイヤ</h2>
  <input type="checkbox" id="refuge" checked /> 一次避難所<br>
  <input type="checkbox" id="area" checked /> 想定浸水区域<br>
  <p>凡例</p>
  <img src="https://yamauchi-inochu.github.io/arcgis_api/img/legend_e.png">
  <p>このデータは越前市オープンデータを加工したものです。</p>
</span>

```

次に`<script>`内を以下のようにする。

```JavaScript
//requireに"dojo/onを追加し、fuctionにon"を追加する

require([
  "esri/Map",
  "esri/views/MapView",
  "esri/widgets/ScaleBar",
  "esri/widgets/Compass",
  "esri/layers/KMLLayer",
  "dojo/on",
  "dojo/domReady!"

], function(
  Map,
  MapView,
  ScaleBar,
  Compass,
  KMLLayer,
  on
) {

  const area = new KMLLayer({
        url:"https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/flood_assumed_area.kml",
        id:"area"
      });

  const refuge = new KMLLayer({
        url:"https://raw.githubusercontent.com/gis-oer/datasets/master/vector/kml/cesium/refuge.kml",
        id:"refuge"
      });

  const map = new Map({
    basemap: "streets",
    layers: [area,refuge]

  });

  const view = new MapView({
    container: "viewDiv",
    map: map,
    center: [136.1688, 35.9032],
    zoom: 11
  });

const scalebar = new ScaleBar({
  view: view,
  unit: "dual"
});

view.ui.add(scalebar, "bottom-left");

const compass = new Compass({
  view: view,
});

view.ui.add(compass, "up-left");

//レイヤのオン、オフを指定する
const areaToggle = document.getElementById("area");
const refugeToggle = document.getElementById("refuge");

on(areaToggle, "change", function() {
      area.visible = areaToggle.checked;
  });
on(refugeToggle, "change", function() {
      refuge.visible = refugeToggle.checked;
  });

});
```

[▲メニューへもどる]

#### ライセンスに関する注意事項
本教材で利用しているキャプチャ画像の出典やクレジットについては、[その他のライセンスについて]よりご確認ください。

[その他のライセンスについて]:../../license.md
[▲メニューへもどる]:./arcgisapi4js.md#Menu
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
