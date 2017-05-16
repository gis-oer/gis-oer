# QGIS+Python初級
　本教材は、QGIS+Python入門の教材です。以下では、QGISのPythonモジュールとコンソール機能を利用した処理について解説します。Pythonの入門書などで基礎を学んでから、本教材をすすめると学習がしやすいです。Pythonコンソールの使用法については、[QGISビギナーズマニュアル](../QGISビギナーズマニュアル/QGISビギナーズマニュアル.md)を参考にしてください。


**Menu**
* [エンコーディング変換](#エンコーディング変換)
* [座標変換](#座標変換)
> 上記の教材は、[OSGeo財団日本支部　QGISセミナー・中級編 Ver. 2.4版](http://www.slideshare.net/FOSS4G_MEXT/qgis-39125122)を参考に作成しています。

* [値の検索と書き出し](#値の検索と書き出し)

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

```python
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

## ジオメトリの表示
　以下では、QGISのPythonコンソールを用いてポリゴンデータのジオメトリを取得する手法について解説しています。
> [QGIS Tutorials and Tips](QGIS Tutorials and Tips)の[Getting Started With Python Programming](http://www.qgistutorials.com/en/docs/getting_started_with_pyqgis.html)を参考に作成

```python
#pythonコンソールを開きレイヤウィンドウでレイヤを選択しておく
ly = iface.activeLayer()

#ジオメトリを取得して表示する
for geom in ly.getFeatures():
    geometry = geom.geometry()
    print geometry.asPolygon()
```

## 値の検索と書き出し
　PythonによるCSVファイルの文字列の検索と書き出しは、以下のように行うことができる。また、以下はQGISを使用していない。

※ 日本語が含まれている場合、CSVのエンコードをUTF-8にしておく


```python

# pandasをインストールする
pip install pandas

# pythonを立ち上げる
python

# ディレクトリの指定（os）、csv読み込み(pandas)のモジュールを読み込む
import pandas as pd
import os

# 作業ディレクトリの指定
os.chdir("作業ディレクトリのパス")

# aedにcsvを読み込む
aed = pd.read_csv("データ名.csv")

# 読み込んだCSVの表示
print aed

# 値の検索とaedcsvへの書き込み
aed.query("列名 == '検索したい値'") 
aedcsv = aed.query("列名 == '検索したい値'") 
print aedcsv

# csvに書き出す
aedcsv.to_csv("test.csv")

```

※　書き出されたデータは、utf-8のため、日本語が含まれていると文字化けがおきる（テキストエディタ等で変換が必要）
