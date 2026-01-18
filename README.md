# GSD Calculator

ドローン測量・点検業務のための、**画素密度（GSD）** と **モーションブラー** を計算するWebアプリです。

**iPhoneやAndroidのホーム画面に追加することで、オフラインでも動くアプリとして利用可能です。**

## デモ・使い方
**[アプリを開く (Click here)](https://aki0290.github.io/GSD_calc/)**

---

## 主な機能

1.  **GSD（地上画素寸法）の計算**
    * 対地高度（距離）から、GSD（何mm/pxか）を算出します。
2.  **高度の逆算**
    * 「GSD 5mm以下で撮りたい」といった場合、必要な高度を逆算します。
3.  **モーションブラー（移動ブレ）判定**
    * 飛行速度とシャッタースピードを入力すると、写真が何cmブレるかを計算。
    * GSDと比較し、ブレが許容範囲内か（緑）、画質劣化するか（赤）を自動判定します。
4.  **プリセット保護機能 (Safe Mode)**
    * 登録済みの機体を選択中は、FOV（画角）などの数値を誤って書き換えないよう自動ロックされます。
5.  **カスタム機材登録**
    * 自分の持っている機材やレンズを登録し、ブラウザに保存できます。
6.  **PWA対応 (オフライン動作)**
    * 電波のない山間部や現場でも使用可能です。

---

## iPhone / Android へのインストール方法

このツールは **PWA (Progressive Web App)** に対応しています。アプリストアを経由せず、以下の手順でインストールできます。

### iPhone (iOS) の場合
1.  Safariで[アプリのURL](https://aki0290.github.io/GSD_calc/)を開く。
2.  画面下部の **「共有ボタン（四角から矢印）」** をタップ。
3.  メニューをスクロールし、**「ホーム画面に追加」** を選択。
4.  右上の **「追加」** をタップ。
5.  ホーム画面にアイコンが追加され、全画面アプリとして起動します。

---

## 対応機種・プリセット

**DJI Enterprise / Zenmuse**
* Zenmuse P1 (24mm / 35mm)
* Zenmuse L2 (RGB)
* Zenmuse H20
* Matrice 4T / 4D / 30T / 300 RTK

**DJI Mavic Series**
* Mavic 3 Enterprise (Wide)
* Mavic 3 / 3 Pro / Classic
* Mavic 2 Pro / Zoom / Enterprise

**Phase One**
* iXM 100MP (80mm)

> ※ リストにない機材も「手動入力」または「カスタム登録」で利用可能です。

---

## 🛠️ 開発・カスタマイズ

このアプリは単一の HTML ファイル (`index.html`) で動作しています。特別なビルド環境は不要です。

### 新しい機材をコードに追加する場合
`index.html` 内の `defaultData` オブジェクトを編集してください。

```javascript
const defaultData = {
    // 新しいドローンの追加
    "my_new_drone": { 
        name: "My New Drone (24mm)", 
        sw: 17.3,  // センサー横幅(mm)
        sh: 13.0,  // センサー縦幅(mm)
        pw: 5280,  // 横画素数(px)
        fov: 84    // 水平画角(deg)
    },
    // ...
};