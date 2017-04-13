# QGIS+Python初級
　本教材は、QGIS+Python入門の教材です。以下では、QGISのPythonモジュールとコンソール機能を利用した処理について解説します。Pythonの入門書などで基礎を学んでから、本教材をすすめると学習がしやすいです。Pythonコンソールの使用法については、[QGISビギナーズマニュアル](../QGISビギナーズマニュアル/QGISビギナーズマニュアル.md)を参考にしてください。

>本教材は、[OSGeo財団日本支部　QGISセミナー・中級編 Ver. 2.4版](http://www.slideshare.net/FOSS4G_MEXT/qgis-39125122)を参考に作成しています。


**Menu**
* [エンコーディング変換](#エンコーディング変換)
* [座標変換](#座標変換)

## エンコーディング変換
　以下では、複数のデータのエンコーディングを一括で変換する手法について解説します。Shift-JISのデータをutf-8に変換しています。この処理を行う前にQGISでエンコーディングをShift-JISに指定し、適当なデータを読み込んでおいてください（データの読み込みのエンコーディングをShift-JISにするため）。

### モジュールをインポートする

```python
import qgis.core
import os
import glob
```

### データのパスとデータを変数に代入する
以下を進めるには、任意の場所にフォルダを作成し、同じエンコーディングのデータ(シェープファイル)を複数個、移動しておく必要があります。

```python
path="C:/Users/ユーザー名/Desktop/data/test"
#layersにデータを読み込む
layers = glob.glob(os.path.join(path, r'*.shp'))
layers
```
pathにデータのある場所を代入し、layerにシェープファイルを代入する。
layersにと入力するとデータが表示される。

## データ分のループをかける
layersからデータを一つずつとりだし、`for`文でデータ数分のループ処理を行う。
ループ処理の間は、`for`以下をタブで字下げする。
以下のように設定し、レイヤを書き出す。

```pyhon

for layer in layers:
    print("Input: "+ layer)
    #名前の設定
    out=layer.replace(".shp","_utf8.shp")
    #パスの設定
    name=os.path.basename(layer).replace(".shp","")
    #レイヤ情報（レイヤ名パスベクトルデータ）
    vl=QgsVectorLayer(layer, name, "ogr")
    #上記の設定でレイヤを書き出す。レイヤ、書き出し先、エンコーディング、crs、ファイル形式を指定する
    QgsVectorFileWriter.writeAsVectorFormat(vl,out,"utf-8",vl.crs(),"ESRI Shapefile")
    print("Output"+out)
```

書き出したデータをQGISで読み込み、エンコーディングが変わっているか確認する。


## 座標変換
　以下では、エンコーディング変換の処理を少し変え座標変換をする処理について解説しています（CRS:4612→2451）。エンコーディング変換の処理と同じようにデータを読み込んでおいてください。

```python
#モジュールを読み込む
import qgis.core
import os
import glob

#データのある場所のパスを設定する
path="C:/Users/ユーザー名/Desktop/data/test/"
#変換するCRSを設定
exp_crs = QgsCoordinateReferenceSystem(2451,QgsCoordinateReferenceSystem.EpsgCrsId)
#データを読み込み表示する
files = glob.glob(os.path.join(path, r'*.shp'))
files
#座標変換のループ処理をする
for file in files:
    print("Input: "+ file)
    out=file.replace(".shp","_9kei.shp")
    name=os.path.basename(file).replace(".shp","")
    vl=QgsVectorLayer(file, name, "ogr")
    #新規にデータを書き出す
    QgsVectorFileWriter.writeAsVectorFormat(vl,out,"utf_8", exp_crs, "ESRI Shapefile")
    print("Output: "+ out)
```

書き出したデータをQGISで読み込み、座標変換ができているか確認する。
