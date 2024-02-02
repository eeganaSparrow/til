## Tailwind CSSについて
# 1. コンポーネント化＋Tailwind CSS利用の準備
* 機能ごとにコンポーネントを分割して設計
    * コンポーネントの関係を把握する作業
* <head>タグ内にviteのリンクを追加  
    * @vite(‘resources/css/app.css’)
    * @vite(‘resources/js/app.js’)
# 2. propsの指定
* {{ $変数名 }}で指定
* {{ $変数名 ?? ‘値’ }}で変数がないときの値を指定
* 利用時は、<x-〇〇 変数名=“”>でprops指定
# 3. 基本の書き方（デザイン項目ごとに分けて書く）
* レイアウト
    * flex
        * flex-wrap（折り返し）
        * justify-end（位置）
        * inline-flex
    * block
* 位置決め
    * p（p-4で1rem,16px）
    * m
    * w（w-fullは100%）
    * max-w-screen-sm（画面最大幅）
    * items-center
* 文字
    * text-{color}（色）
    * text-left（文字位置）
    * leading-none（line-height）
    * font-semibold（太さ）
* 背景
    * bg-{color}
* 枠線
    * border
    * border-{color}
    * rounded-md（丸み）
    * shadow-sm（影）
    * ring-2（周縁）
    * ring-offset-2（周縁）
* ステート
    * focus:
        * ring-{color}（周縁）
        * border-{color}（枠線）
    * メディアクエリ
        * sm:text-sm（最小値を設定）
        * lg:rounded-full（最大の丸み）
    * hover:
        * bg-{color}
* SVGアイコン
    * https://heroicons.com/
    * 使用できるアイコンが上のようなサイトにあるので、それを貼り付けると導入できる
* 【備考】
    * div要素はレイアウトと位置をデザインすることが多いのかも
    * 全体の表示幅を制限したい場合
        * コンポーネントを用意
        * divで囲んで、レイアウトを設定
        * その中のdivで最大幅の設定
# 4. その他
* @props([変数 => ‘’])
    * 受け取る変数とそのデフォルト値を指定する
* themeの振り分け
    * php関数で振り分けるので、@phpディレクティブを指定
    * 関数の戻り値にmatch関数を指定し、themeの振り分け
    * theme適用箇所で関数を呼び出して利用
