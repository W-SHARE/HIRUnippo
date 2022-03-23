# railsをherokuで公開しよう

## 手順

https://qiita.com/kazukimatsumoto/items/a0daa7281a3948701c39

基本的にこれを見れば大丈夫。これを軸に補足説明しようと思う。

```
＄brew tap heroku/brew && brew install heroku

＄heroku login
```

これで環境にherokuをインストールしてアカウントを紐付けしよう。

このサイトではgitと紐付ける方法を説明しているが、githubと紐付けたほうが楽である。

https://www.youtube.com/watch?v=26MmHYI4xCQ

これを参考すればgithub経由のデプロイ設定ができる。

gitでやる人はエラーが出る可能性があるのでこちらを参考にしていただきたい。

https://qiita.com/m6mmsf/items/fb8a8672df98bdb59c9c

herokuとローカルのbundlerのバージョンの相違について、herokuのエラーメッセージを確認の上、以下の方法でバージョンを揃えてほしい。

https://qiita.com/___fff_/items/8b62633b59d7d72e6719

Gemlockの扱いが厄介だが、上記のパターンをすべて試せば必ず成功する。

そしたらいよいよデプロイである。上記YouTubeの解説動画であった通り、デプロイと同時に自動でマイグレーションしてくれると楽なので、設定しよう。

https://qiita.com/d0ne1s/items/736bdc0bc9debd74de1f

seedも自動でやってほしいので今方法を調べている。手動でやる方法は、herokuの画面右上MoreボタンのRun consoleで

```
rake db:seed
```

を入力していただきたい。マイグレーションもここからできる。

データベースはherokuだとPostgreSQLであり、rails付属はsqlite3なので、勝手が少し違ってくる。

herokuアプリ内のdatacripでクエリを書くことによってデータベースを閲覧できる。いろいろいじってみてほしい。

アプリの更新は、githubに変更をpushした後、再度デプロイボタン押せば良い。

gitでやる人は以下の方法。

https://qiita.com/MNK0910/items/5f47fed4a07b9f75944d

herokuの説明は以上である。アプリが公開できるとモチベもあがるものだ。

Googleの検索結果で出てくるともっとモチベがあるなぁと思い、調べてみたら以下の興味深い結果が得られた。

https://teratail.com/questions/188432

頑張ってアプリを伸ばそう！！！
