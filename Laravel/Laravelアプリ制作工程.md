1. 開発環境の作成
    1. アプリ作成（実行後、5分ほど）
        * curl -s "https://laravel.build/{アプリ名}?with={サービス名memcachedとか}” | bash
    2. アプリ立ち上げ
        * sail up -d（./vendor/bin/sail up）
    3. ブラウザで確認
        * http://localhost