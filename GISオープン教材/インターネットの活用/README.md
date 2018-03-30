# インターネットにおけるGIS技術の活用の教材
　この教材は、インターネットにおけるGIS技術の活用の教材です。アプリケーションやライブラリを用いてWEB地図を作成する手法やデータの作成手法について解説しています。プログラミングの基礎やサーバーの設定については解説していません。この教材では、GitHubのGh-pagesを利用して解説している場合があります。GitHubについては、[GitHubビギナーズマニュアル]を参照してください。また、このページではGIS初学者向けに、WEB地図のコンテンツを利用する際の注意事項についてもまとめています。

## 教材一覧

### WEB MAP操作・作成入門 (WEBマップGUIツール、サービスの利用法)
- [Carto](./CartoDB/Carto.md#Carto)
- [地理院地図](./地理院地図/地理院地図.md)
- [OpenStreetMap(= 参加型GISと社会貢献の教材)](../26_参加型GISと社会貢献/26_参加型GISと社会貢献.md)
- [Googleマイマップ](./Googleマイマップ/Googleマイマップ.md)

### WEB MAP操作・作成入門 (WEBマップライブラリの利用法)
- [Leaflet](./Leaflet/Leaflet.md)
- [Cesium](./Cesium/Cesium.md)
- [D3.js](./D3.js/D3.js.md)
- [OpenLayers](./OpenLayers/OpenLayers.md)

### データ作成入門
- [CZML](./CZML/CZML.md)
- [KML](./KML/KML.md)
- [GeoJSON](./GeoJSON/GeoJSON.md)

### タイル地図入門
- [タイル地図（ラスタ）](./rastertile/rastertile.md)

### データ解析入門:準備中
- [GoogleEarthEngine](#)

### GitHub
- [GitHubビギナーズマニュアル](./GitHubビギナーズマニュアル/GitHubビギナーズマニュアル.md)

## Web地図サービスと利用規約
　他者が作成したコンテンツを利用する場合は、著作権やライセンスを遵守する必要があります。
行政や企業などが配信しているタイル地図などのWeb地図コンテンツは、それぞれのサービスごとに使用できる範囲が利用規約で定められています。そのため、これらを使用する際には、それぞれの利用規約に従う必要があります。以下では、Web地図サービス（特にタイル地図）をとりあげ、それぞれのサービスにおける特徴についてまとめています。

### Web地図サービスの利用について
以下の表は、代表的なWeb地図サービス（特にタイル地図）の利用条件を比較したものです。それぞれのサービスごとに無償利用可能な範囲や条件が異なることを確認してください。各サービスの詳細は、それぞれの利用規約を参照してください。

|サービス|無償利用|出典・帰属|地図画像（静的地図）の複製・配布|利用時の注意事項|詳細(URL)|
|:---|:---|:---|:---|:---|:---|
|地理院タイル|可|「国土地理院」、「地理院タイル」の表記が必要|可（タイルによって申請が必要な場合がある）|国土地理院コンテンツ利用規約の範囲内で利活用が可能。基本測量成果を含むタイルは複製、利用にあたって申請が必要となる場合がある。|[地理院タイルのご利用について](https://maps.gsi.go.jp/help/use.html)|
|Google Maps|可（一定量を超えると有償）|Google とデータプロバイダの権利帰属を表記（例：「Map data ©2015 Google」）|基本的には不可|利用条件が複雑なため、使用時には深く使用許諾を読み込む必要がある。代表的な注意点として、Webサイト等でGoogle マップ等を画像として利用することができない一方で、Web地図としての埋め込みは可能であること等があげられる。商業利用と個人利用で制約が異なる点にも注意する必要がある。|[Google マップ、Google Earth、ストリートビューの使用](https://www.google.co.jp/intl/ja/permissions/geoguidelines.html)|
|OpenStreetMap|可（過度なアクセスを制限）|「© OpenStreetMap contributors」の表記|可|OpenStreetMapのサーバは全て寄付によるリソースで運用されているため、ヘビーユースが禁止されている点に注意が必要である。|[JA:タイル利用規約](https://wiki.openstreetmap.org/wiki/JA:タイル利用規約)|
|Bing Maps|可（有償ライセンスもあり、実装方法に応じたライセンス形態）|ロゴと著作権条項の記載|[Microsoft Print Rights](https://www.microsoft.com/en-us/maps/product/print-rights)に従う|日本語の利用規約が公開されていないため、細かな点の解釈が難しい。|[Microsoft® Bing™ Maps Platform APIs' Terms Of Use](https://www.microsoft.com/en-us/maps/product)|


上記の表は、2018年3月現在の情報です。各サービスを利用する場合、利用規約を確認の上、使用してください。また、上記について不適切な表現や誤りがある場合は、この[Markdown](https://github.com/gis-oer/gis-oer/blob/master/GISオープン教材/インターネットの活用/rastertile/rastertile.md)Pull Requestをいただくか、issuesにてコメントをいただけますと幸いです。

> 上記の表の作成にあたって、各サービスの利用規約の他、  
[Qiita記事　行政サイトでウェブ地図を使う際の注意点などまとめ（@nyampire氏 作成）](https://qiita.com/nyampire/items/5fd06107f25bc12a526f)、  
[森林土木memo　地理院の地図コンテンツの利用規約がわかりづらい？](http://koutochas.seesaa.net/article/422316884.html)、  
[ArcGIS Online ヘルプ 著作権の表示(ESRI社 作成)](http://doc.arcgis.com/ja/arcgis-online/reference/display-copyrights.htm)、  
[Bing Maps API のよくある質問 (Microsoft 社)](https://www.xlsoft.com/jp/products/bing_maps/faq.html)  
等を参考にした。
