# nginxの設定

## Basic認証の設定
* auth_basic 認証名 | off;
    * 認証名は任意の文字列
* auth_basic_user_file ファイルパス;
    * パスワードファイルのパスを指定する
    * 作成方法（パスワードが暗号化される）
        * htpasswd -c /opt/homebrew/etc/nginx/.htpasswd ユーザー名
        * パスワードを入力
* 一度ログインするとキャッシュされる
* キャッシュを削除する方法は不明。少し時間が経つと切れていたりする。

## 

