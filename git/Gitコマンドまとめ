# Gitコマンドまとめ
* gitでの管理
    * git init：リポジトリの初期化
    * git status：状態確認。基本中の基本らしい
    * git add：ステージング
    * git commit：コミット
        * -mないなら、エディタが開く
        * ––amendでコミットメッセージ修正（直前）
        * -aで、ステージングとコミットを同時にできる
    * git log：コミットログが見れる
        * ––pretty=shortとか色々、表示を変えれる
        * ––graphでグラフが見れる
        * -p：特定のファイルの差分を見れたりする
    * git diff：ワークツリーとステージング領域の差分の確認
        * HEADをつけるとワークツリーと最新コミットの差分
* ブランチの利用
    * git checkout
        *  -b ブランチ名：ブランチ作成とチェックアウト
        * -：前のブランチに戻る
    * git merge
        * ––no-ff：fast-forwardでもマージコミットが作られる
* コミットの変更
    * git reset ––hard ハッシュ名：歴史を戻る
    * git reflog：歴史を探す
    * mergeでコンフリクト起きたら、正しい内容に修正して解消
* 歴史の改ざん
    * git rebase -i HEAD~2：2つ前までを対象とする
    * エディタで揉み消す履歴のpickをfixupに書き換える
* リモートリポジトリの利用
    * git remote add origin GitHubのリポジトリパス：リポジトリ登録
    * git push：リポジトリ送信
        * -uを付けておくと、pullのときに取得するブランチが設定される
    * git clone：リポジトリの取得
    * git branch -a：リモートリポジトリのブランチも見れる
    * git pull：リモートの最新をローカルに入れる
