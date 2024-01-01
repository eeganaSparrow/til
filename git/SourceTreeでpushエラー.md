## SourceTreeでpush時にエラー

- エラー内容  
`git --no-optional-locks -c color.branch=false -c color.diff=false -c color.status=false -c diff.mnemonicprefix=false -c core.quotepath=false -c credential.helper=sourcetree push -v --tags origin refs/heads/master:refs/heads/master 
Pushing to https://github.com/eeganaSparrow/mao-seminar.git
remote: Permission to eeganaSparrow/mao-seminar.git denied to eeganaSparrow.
fatal: unable to access 'https://github.com/eeganaSparrow/mao-seminar.git/': The requested URL returned error: 403
Completed with errors, see above`

- 解決方法
1. GitHubで、以下のようにメニューを辿り、トークンを生成＋コピー  
`Settings` ＞ 左側メニューの`Developer settings` ＞ `Personal access tokens` ＞ `Tokens(classic)` ＞ `Generate new token`  
※トークン生成時に、repoスコープにチェックを入れておく。
2. SourceTreeで、トークンを設定  
設定 ＞ リモート ＞ 設定するパスを編集  
`https://git.com/~~~` というパスを、`https://トークン名@git.com/~~~` としてトークンを設定する。
