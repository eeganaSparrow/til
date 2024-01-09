# Webページの制作手順（フルスクリーン）
## １．画面レイアウトを考える
1. どんなページを作るか考える
    - サンプル画面を作る
    - 必要な画像を準備する
2. コードの下準備
    1. ブロック要素に分ける
        - headerとかdivに分割
    2. 中身のタグを当てはめる
        - h1、p、aなど

## ２．htmlの作成
1. `<head>`の記述
    1. `<meta>`
    2. `<link>`
        - ress.css
        - Webフォント
        - CSS
2. `<body>`の記述
    1. ブロック要素の記述
    2. 中身のタグを記述
        - デザインしたい箇所にはclassやidを指定
        - class名・id名はどこの部位なのか分かるように名付ける
    3. 大体、１ブロック書けたらCSSで整える

## ３．CSSの作成
1. @charset “UTF-8”; を書き、文字化けを防ぐ
2. 共通部分の記述
    1. html
        - font-size:100%で、ユーザー設定に準じるフォントサイズになる
    2. body
        - フォントの指定（font-family）
        - 行高さの指定（line-height）
        - 文字色の指定（color）
    3. a
        - 傍線の指定（text-decoration）
    4. img
        - 画像の大きさの指定（max-width）
3. 詳細部分のデザインを指定（以下参考まで）
    - レイアウト
        - 並べ方（display: flex）
        - 位置（justify-content）
    - 文字
        - サイズ
        - 位置
        - 大文字・小文字
        - 太さ
    - 余白
        - マージン
        - パディング
    - リスト
        - リストスタイル
    - ボタン
        - 背景色
        - 文字色
        - 角丸（border-radius）
        - 余白
        - 色変化（hoverセレクター）
4. １ブロック分書けたら、２-２で次のブロックを書く

## ４．背景画面を入れるなら
1. html部分
    - 全体を`<div>`で囲む
    - idやclassを指定
2. css部分
    - background-size: cover; で画面いっぱい
    - background-position: center top; でウィンドウに追随

## ５．ファビコンを作るなら
1. ファビコンを用意
    - ファビコン生成サービスがあるらしい
    - RealFaviconGenerator
2. linkでiconを指定して埋め込む
