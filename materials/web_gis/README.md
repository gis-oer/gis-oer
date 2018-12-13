# インターネットにおけるGIS技術の活用の教材
　この教材は、インターネットにおけるGIS技術の活用の教材です。アプリケーションやライブラリを用いてWEB地図を作成する手法やデータの作成手法について解説しています。プログラミングの基礎やサーバーの設定については解説していません。この教材では、GitHubのGh-pagesを利用して解説している場合があります。GitHubについては、[GitHubビギナーズマニュアル](./GitHub/GitHub.md)を参照してください。また、このページではGIS初学者向けに、WEB地図のコンテンツを利用する際の注意事項についてもまとめています。

## 教材一覧

### WEB MAP操作・作成入門 (WEBマップGUIツール、サービスの利用法)
- [Carto](./CartoDB/Carto.md)
- [地理院地図](./gsimap/gsimap.md)
- [OpenStreetMap(= 参加型GISと社会貢献の教材)](../26/26.md)
- [Googleマイマップ](./Google_mymap/Google_mymap.md)

### WEB MAP操作・作成入門 (WEBマップライブラリの利用法)
- [Leaflet](./Leaflet/Leaflet.md)
- [Cesium](./Cesium/Cesium.md)
- [D3.js](./D3js/D3js.md)
- [OpenLayers](./OpenLayers/OpenLayers.md)
- [ArcGIS API for JavaScript](./arcgisapi4js/arcgisapi4js.md)

### データ作成入門
- [CZML](./CZML/CZML.md)
- [KML](./KML/KML.md)
- [GeoJSON](./GeoJSON/GeoJSON.md)

### タイル地図入門
- [タイル地図（ラスタ）](./rastertile/rastertile.md)

### データ解析入門:準備中
- [GoogleEarthEngine](#)

### GitHub
- [GitHubビギナーズマニュアル](./GitHub/GitHub.md)

## Web地図サービスと利用規約
　他者が作成したコンテンツを利用する場合は、著作権やライセンスを遵守する必要があります。
行政や企業などが配信しているタイル地図などのWeb地図コンテンツは、それぞれのサービスごとに使用できる範囲が利用規約で定められています。そのため、これらを使用する際には、それぞれの利用規約に従う必要があります。以下では、Web地図サービス（特にタイル地図）をとりあげ、それぞれのサービスにおける特徴についてまとめています。

### Web地図サービスの利用について
以下の表は、代表的なWeb地図サービス（特にタイル地図）の利用条件を比較したものです。それぞれのサービスごとに無償利用可能な範囲や条件が異なることを確認してください。各サービスの詳細は、それぞれの利用規約を参照してください。

|サービス|無償利用|出典・帰属|地図画像（静的地図）の複製・配布|利用時の注意事項|詳細(URL)|
|:---|:---|:---|:---|:---|:---|
|地理院タイル|可|「国土地理院」、「地理院タイル」の表記が必要|可（タイルによって申請が必要な場合がある）|国土地理院コンテンツ利用規約の範囲内で利活用が可能。基本測量成果を含むタイルは複製、利用にあたって申請が必要となる場合がある。|[地理院タイルのご利用について](https://maps.gsi.go.jp/help/use.html)|
|Google Maps|可（一定量を超えると有償）|Google とデータプロバイダの権利帰属を表記（例：「Map data ©2015 Google」）|基本的には不可|利用条件が複雑なため、使用時には深く使用許諾を読み込む必要がある。代表的な注意点として、Webサイト等でGoogle マップ等を画像として利用することができない一方で、Web地図としての埋め込みは可能であること等があげられる。商業利用と個人利用で制約が異なる点にも注意する必要がある。|[Google マップ、Google Earth、ストリートビューの使用](https://www.google.co.jp/intl/ja/permissions/geoguidelines.html)|
|OpenStreetMap|可（過度なアクセスを制限）|「© OpenStreetMap contributors」の表記|可|OpenStreetMapのサーバは全て寄付によるリソースで運用されているため、ヘビーユースが禁止されている点に注意が必要である。|[Tile Usage Policy](https://operations.osmfoundation.org/policies/tiles/)|
|Bing Maps|可（有償ライセンスもあり、実装方法に応じたライセンス形態）|ロゴと著作権条項の記載|[Microsoft Print Rights](https://www.microsoft.com/en-us/maps/product/print-rights)に従う|日本語の利用規約が公開されていないため、細かな点の解釈が難しい。|[Microsoft® Bing™ Maps Platform APIs' Terms Of Use](https://www.microsoft.com/en-us/maps/product)|


上記の表は、2018年3月現在の情報です。各サービスを利用する場合、利用規約を確認の上、使用してください。また、上記について不適切な表現や誤りがある場合は、この[Markdown](./README.md)へPull Requestをいただくか、issuesにてコメントをいただけますと幸いです。

> 上記の表の作成にあたって、各サービスの利用規約の他、
[Qiita記事　行政サイトでウェブ地図を使う際の注意点などまとめ（@nyampire氏 作成）](https://qiita.com/nyampire/items/5fd06107f25bc12a526f)、
[森林土木memo　地理院の地図コンテンツの利用規約がわかりづらい？](http://koutochas.seesaa.net/article/422316884.html)、
[ArcGIS Online ヘルプ 著作権の表示(ESRI社 作成)](http://doc.arcgis.com/ja/arcgis-online/reference/display-copyrights.htm)、
[Bing Maps API のよくある質問 (Microsoft 社)](https://www.xlsoft.com/jp/products/bing_maps/faq.html)
等を参考にした。
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
