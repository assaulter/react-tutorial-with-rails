# Railsを使ってreactjsのサンプルを作成

[the React tutorial](http://facebook.github.io/react/docs/tutorial.html).

## 起動方法
```
$ bundle install
$ bundle exec rake db:migrate
```

## 説明

### Rails

Railsは画面表示用のコントローラーと、ReactからコールされるAPIコントローラーの２つを持つ

* DashboardsController → viewをrenderするだけ
* Api::CommentsController
  * #index : ActiveRecordを使ってすべてのコメントを取得。render jsonで、jsonを返す。
  * #create : コメントを追加。追加された結果を返す

### React
assets/javascripts/components/sample.js.jsx が本体

構造としてCommentBoxがCommentListと一つのCommentFormを持つ。

CommentListは複数のCommentを持つ

#### コメント一覧を表示する
ライフサイクルイベントのcomponentDidMount内でloadCommentsFromServerをコール

stateに一覧データを持つ

データをCommentListに渡す。

CommentListは内部でdataを用いてn*のCommentを生成。

#### コメントを追加する
CommentFormがイベントを取得。

処理はCommentBoxにデリゲートする。
