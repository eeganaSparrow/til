# Laravel入門のメモ

## ビューとテンプレート
* ディレクティブ
    * @yield
        * セクション要素を表示するもの
        * ベース側に書く
    * @extends
        * 利用するベースを記述する
    * @section
        * 利用側で書く場合
            * ベースの@yieldに内容を渡す
        * ベース側で書く場合
            * @parentで親要素に追記という形式（指定ないなら、上書き）
            * @showの部分に利用側の記述が入る
    * @component
        * @slotを使って変数を渡せる
    * @include
        * 定型のコンテンツや変数が少ない場合などが利用場面
    * @each
        * 指定したテンプレートに配列を順番に渡す
* ビューコンポーザ
    * ビューにデータを結合する仕組み
    * ビューのための処理を分離することができる
    * ビューコンポーザの利用
        1. プロバイダー作成
            * sail artisan make:provider 〜
        2. 処理の記述
            1. boot()に記述
            2. View::composer(テンプレート, ビューコンポーザ（クロージャーかクラス）)
                1. クロージャーの場合
                    * function($view){$view->with(‘変数’, ‘値’)}
                2. ビュークラスの場合
                    * Composerクラス作成
                    * composeメソッドの記述
        3. プロバイダー登録
            * config/app.phpのproviders
        4. 利用
            * テンプレートで{{ 指定した変数 }}
## バリデーション
* バリデータの作成方法
    * コントローラでValidatorクラスのmake()メソッドを使う
        * $varidator = Validator::make($request->all(), [ バリデーション ]);
    * formにリダイレクトしないvalidatorを作ることができる
        * if($validator->fails())で振り分け
* クエリ文字列のバリデーション
    * Validatorクラスのquery()メソッドを使う
        * $varidator = Validator::make($request->query(), [ バリデーション ]);
* メッセージのカスタマイズ
    * FormRequestのmessages()メソッドをオーバーライドして、連想配列でメッセージを指定
    * または、Validatorクラスのmake()の第3引数でメッセージ配列を指定
## データの検索
* モデル名::find(整数)・・・idに一致するレコードを取り出す
* モデル名::where(名前, 値)・・・名前と値が一致するレコードを取り出す
* スコープの分離
    * ローカルスコープ
        1. モデル内にscope名前($query, 引数)メソッドを追加する
        2. where()などの処理を記述
        * 複数設定して組み合わせることもできる
    * グローバルスコープ
        1. モデル内にprotected static function boot()メソッドを追加
            * boot()はモデルの初期化専用メソッド
        2. 中身に、parent::boot()、static::addGlobalScope(検索対象, Builder利用のクロージャ)
            * Scopeクラスを使うなら、addGlobalScope(Scopeのインスタンス)でもいい
        * モデル利用時にいつもグローバルスコープが適用される
    * Scopeクラスの利用
        * Scopeクラスを作成
        * apply($builder, $model)メソッドを作成
## フォーム
* 非表示フィールド
    * フォーム送信時、CSRF用の非表示フィールドがリクエストに追加されている
    * これを削除するには、unset()でリクエストの’_token’を指定する・・・削除して問題ないのか？
* fill()メソッド
    * フォームの値をまとめて設定できる
## RESTful
* RESTfulではCRUDは全て同じアドレス。HTTPメソッドの違いによって処理を分けている。
* Resousefulを導入すれば、RESTfulも満たされる指定する
    1. make:controllerのオプションで、––resourceを指定する
    2. ルートにRoute::resourceを指定すると、７つのメソッドが全て登録される
## セッションの利用
1. セッションテーブルの作成
    * sail aritsan session:table
2. セッションの保存先を指定
    * config/session.phpのdriverでdatabaseを指定
    * .envファイルのSESSION _DRIVERにdatabaseを指定
3. セッションのメソッドを作成
    * セッションの保存
        * $request->session()->put(セッション名, 値)
    * セッションの取得
        * $request->session()->get(セッション名)
## ペジネーションの利用
1. ペジネーションのメソッドを利用
    * simpllePaginate(表示数)
        * 前後のページ遷移を利用できる
    * paginate(表示数)
        * ページ番号で遷移できるようになる
2. ブレードでlink()メソッドを利用
    * {{ $item->link() }}などとすると、ページ番号のパラメータがアドレスに追加される
3. リンクのテンプレート
    * テンプレートの導入
        * sail artisan vendor:publish —tag=laravel-pagination
        * views/vendor/paginationにテンプレートが作成される
    * Bootstrapの利用
        * ブレードにlinkタグでbootstrapを指定
## ソート順の変更
1. コントローラにsortの処理を追加
    * requestから取り出す
2. ブレードでsortの値が送られるようにする
    * aタグで指定する
    * appends([‘sort’ => $sort])->link()で、リンク先にソート情報を送る設定をする
