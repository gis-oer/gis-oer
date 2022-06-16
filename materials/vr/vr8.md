## UnityでのVRの実装
 UnityのMeta Quest 2向けのアプリを開発のための初期設定が済みましたので、実装作業に入ります。

## 1. Oculusで動作するコントローラー（カメラ）の導入
本教材では、Oculus Integrationのアセットを導入しました。Meta Quest 2で動作させるために、Oculus Integrationに収録されているOculus専用のコンポーネント（カメラ）を利用してみます。

### コンポーネントの追加
ProjectウィンドウのAssets傘下から`Oculusフォルダ＞VRフォルダ＞Prefabsフォルダ`を開いて下さい。`Prefabsフォルダ`に`OVRPlayerController`というPrefab（コンポーネント）が入っています。`OVRPlayerController`を、Hierarchyウィンドウにドラッグ・アンド・ドロップして下さい。すると、シーンに`OVRPlayerController`が追加されます。

### VRのカメラの準備
なお、`OVRPlayerController`には`OVRCameraRig`というカメラが含まれています。`OVRPlayerController`を追加したら、すでに導入したStandard Assetsのキャラクター（つまりカメラ）と、カメラ同士が競合しないようにする必要があります。Hierarchyビューから、Standard Assetsのカメラを削除して下さい。`OVRPlayerController`のみが追加されていることを確認したら、シーンの韮山反射炉と`OVRPlayerController`をそれぞれ近づけて、`OVRPlayerController`のカメラが、韮山反射炉を見るように位置・角度を調整して下さい。直接、マウスで`OVRPlayerController`を移動できない場合は、`OVRPlayerController`を選択した状態で、Unity右側のInspectorウィンドウのPositionなどの数値を入力して、位置を調整して下さい。

### 地面の調整
`OVRPlayerController`を追加しました。その後、Standard Assetsのカメラを利用したときと同様の方法で、`OVRPlayerController`が地面（Plane）の上にいるように、地面の面積や`OVRPlayerController`の位置を調整して下さい。この際、シーンビューで`OVRPlayerController`が空中に浮いていても、下に地面があれば、アプリの実行時に`OVRPlayerController`は重力落下して、地面で止まります。厳密に地面に接地させておく必要はありません。）。

## アプリの動作テスト
ただし、ここで注意しなければいけない点は、PCのUnityのゲームビューでアプリを実行しても、`OVRPlayerController`は正しく動作確認できません。つまり、正しい動作確認のためには、Meta Quest 2に転送する必要がありますので、PCのゲームビューで正しく表示されなくても慌てないで下さい（Meta Quest 2への転送方法は後述）。
上述した方法で、Meta Quest 2へ韮山反射炉のアプリをビルド・転送した場合、Meta Quest 2では、アタマの角度によってVR視線の角度が動きます。また、Meta Quest 2の左コントローラーのスティックで前進・後退と横方向への移動ができます。また、右コントローラーのスティックで、視線の方向も回転できます。
