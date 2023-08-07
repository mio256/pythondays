# 作業ファイルをステージする

```
$ git add ファイル名
$ git add .
```

一括指定はゴミが入らないように注意

## .gitignore

.gitignoreでステージしないファイルを指定することができる

[.gitgnoreの書き方](https://qiita.com/inabe49/items/16ee3d9d1ce68daa9fff)

# ステージの確認をする
```
$ git status
```

コミットにゴミが入らないか確認

## git add の取り消し

### 新規ファイルの取り消し（初回）

```
$ git rm --cached -r .
$ git rm --chahed -r ファイル名
```

### 変更の取り消し（2回目以降）

```
$ git reset HEAD
$ git reset HEAD ファイル名
```

# ステージをコミットする
```
$ git commit -m "emoji_prefix.mdを参考にコミットメッセージ"
```

# コミットをpushする
```
$ git push
```

# ブランチの切り替え
```
$ git checkout ブランチ名
```

# ブランチを切る
```
$ git checkout -b 自分の作りたいブランチ名
作業後↓
$ git add .
$ git commit
$ git push -u origin 自分の作ったブランチ名
```

# やらかし編

### ・間違えて `git add` しちゃったとき

以下のコマンドで特定ファイルをステージングから取り除くことができます

```
$ git reset HEAD ファイル名
```

### ・間違えて `git commit` しちゃった時

直前のコミットを取り消したい場合はソフトリセットを行えば解決できます

```
$ git reset --soft HEAD^
```

### ・過去のコミットメッセージを変更したい時

直前のコミットメッセージを編集する場合は `--amend` オプションで解決できます
以下のどちらかのコマンドを一度実行し、メッセージを修正します

```
$ git commit --amend
$ git commit --amend -m "新しいメッセージ"
```

その後pushする際はforceオプションが必須になります
対象ブランチによってはできない場合があるので注意が必要です

```
$ git push origin ブランチ名 -f
```

### ・間違えて違うブランチで作業しちゃった時

一旦変更差分をstashして退避させます

```
$ git stash
```

次にブランチを切り替えて変更差分を取り出します

```
$ git checkout ブランチ名
$ git stash pop
```


# コミットメッセージ

`:Emoji: Title; Reason; Specificatio; Issue`

作業内容はコードを見ればわかるので、コミットメッセージでは「概要」「変更理由」「意図・仕様」を簡潔にまとめる。

1. Emoji - 内容・種類をひと目で分かるように
2. Title - タイトル（概要）
3. Reason - このコミットをする理由
4. Specification - このコミットの意図や仕様など
5. Issue - 対応するIssue

```
# 🌱 :seedling: Init
# 🔥 :fire: Update
# ✨ :sparkles: New features
# 🐛 :bug: Fix bug
# ⚡️ :zap: Refactor, Improve
# 📚 :books: Docs
# 🔧 :wrench: Config
# 🚀 :rocket: Deploy
# 🧬 :dna: Merge
# 🧪 :test_tube: Test
```

コミットメッセージの書き方は以下の記事を参考にする、ただし中級者向けなので流し見で十分。

[ロジカルなコミットメッセージの書き方](https://zenn.dev/mi0256/articles/1332e1d041cab4)
