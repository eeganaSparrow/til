# URIについて
## URIの概要
* URIはシンプルな構造を持っていて、構造があるからプログラムで処理でき、シンプルであるからアクセスしやすい
    * URIスキーム://ホスト名/パス
* 相対URIは処理が複雑であるから、絶対URIの方がクライアントには親切

## URIの設計
* クールURI（URIの設計方針）
    * 言語に依存させない
    * わかりやすい名詞を使う
    * 変わらないURIが理想
* URI変更時
    * リダイレクトで新いURIに遷移するように設定する
* URIで拡張子を使う
    * コンテントネゴシエーション
        * クライアントの言語設定に適したページをレスポンスするHTTPの機能
    * 1つのリソースが複数の表現を持つ場合、拡張子で振り分けるのはアリ
* マトリクスURI
    * マップの緯度/経度など、同次元のパラメータが複数ある場合に使う
    * 順不同ならセミコロン、順序があるならカンマで区切る
* URI設計時に意識すること
    * URIから内部構造を想像して操作されないように、不透明なURIを心掛けるのがよい
    * URIは寿命が長く、ブラウザで表示されるので、しっかり設計した方がいい