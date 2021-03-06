# 0224蛭川日報

## SHARE_app導入過程

Organizationsアカウント"W-SHARE"を作成し、SHAREリポジトリを作成。

ターミナルにて、/Users/hiru/workspace/rubyonrails/W-SHARE内で以下を実行。

```
rails new SHARE_app
```

作成された/SHARE_appに移動。

```
cd SHARE_app
```

ここがRailsプロジェクトのルートディレクトリになるため、ここでgitの初期化。

```
git init
```

すると、以下のログが出る。

```
Reinitialized existing Git repository in /Users/hiru/workspace/rubyonrails/W-SHARE/SHARE_app
```

Railsはnewすることにより、gitの設定が自動で行われるので、実はgit initする必要がないらしい。

これでgitの初期設定が完了しているので、addしてステージに上げる。

```
git add .
```

この最後の.は、すべてのファイルと言う意味である。その前に、git statusでステージに上げるべきファイルを確認しておくと良い。

そうしたらローカルにコミットする。

```
git commit -m "first commit"
```

次に、リモートリポジトリの登録をする。

```
git remote add origin リポジトリのURL
```

リポジトリのURLはHTTPS通信より、SSL通信のほうがいいだろう。URLはgithubのリポジトリ画面のCodeというところからコピーできる。SSL通信の設定ができていない人は各自ググる。

そうしたら最後に、リモートリポジトリにpushして、ローカルの更新をリモートに反映させる。

```
git push -u origin main
```

いろんなリソースに、mainではなくmasterって書いてあると思うが、最近githubの人権問題で、デフォルトブランチの名称が変更されたのである。後で名前は変えられるが、mainのほうがいいだろう。

この際に以下のエラーメッセージを吐く可能性がある。

```
error: failed to push some refs to "URL"
```

これは、既に作成されているREADME.mdがあるせいである。railsでnewしたときREADME.mdも作成されるので、

```
git push --force origin main
```

で強制的にpushしてしまおう。この際、元からあったREADME.mdは上書きされてしまうので、内容は別のファイルに保存しておこう。

--forceオプションは、バコバコ使ってしまうと、他の人の更新を上書きしてしまうので、無闇矢鱈に使わないどこう。

以上でrailsのnewをgitに反映させる過程は終了である。

## GitHubを用いた開発フローについて

SHARE_appでは、GitHub社が実践しているシンプルなワークフローを採用する。

早速解説していく。リポジトリが既に存在している前提で始めるので注意。gitのローカル環境というか、作業フォルダを予め用意して移動しておこう。

まず、リモート(GitHub)のmainブランチをローカルにcloneする。

```
git clone リポジトリのURL
```

クローンしたrailsのルートディレクトリに移動しよう。

```
cd railsのルートディレクトリ名
```

すでにcloneしている場合は、pullして更新しておこう。

```
git checkout main

git pull
```

いよいよ作業するブランチ(トピックブランチ)を作成する。ブランチ名は、作業内容がわかりやすいものにしよう。まずはローカルで作成し、移動しよう。

```
git checkout -b トピックブランチ名
```

-bオプションを追加することで、作成も同時にできる。checkoutはブランチに移動するコマンドである。

次に、リモートで同名のトピックブランチを作成しよう。

```
git push -u origin トピックブランチ名
```

ここで、ローカルとリモートの名前を揃えないとエラーを吐く。

あとはそのトピックブランチにいることを確認し、ローカルで作業するだけである。

作業が完了したら、内容をaddし、commitしよう。

```
git add .

git commit -m "コミットメッセージ"
```

最後に、リモートにpushして変更を更新しよう。

```
git push
```

お疲れさまでした。

## 学習内容

### Progate

Sass1を完了。Sassとは、CSSの拡張で、だいぶ見通しが良くなる。てか、使わないと損。例えば、

```html
<div class="main">
  <h1>おれ</h1>
  <div class="sanjo">参上</div>
</div>
```

というhtmlがあったとしよう。従来のCSSだと、

```css
.main h1 {
  color: #3f3f3f;
}

.sanjo {
  color: #3f3f3f;
}
```

こんなのが、SCSSだと、

```scss
$iro: #3f3f3f;
.main{
  h1 {
    color: $iro;
  }
  &.sanjo {
   color: $iro;
  }
}
```

みたいなかんじで見通し良くなる。入れ子には、&:hoverとかでできる。あとは、関数作れたり、関数ファイルを読み込んだりできる。(例:_max.scssというファイルを読み込んでいる)

```scss
@import "max";

@mixin ehe($iro) {
  font-size: 15px;
  color: $iro;
  @include aha;
}
```

とかいろいろ。学んでみるといいかもしれない。

###　気になったニュース

ついにロシアがウクライナに侵攻した。第三次世界大戦が始まるかもしれない。

## 西ノ原
最高な日報をありがとう  
第三次世界大戦になったら留学いけないやん。マジでプーチンチンやめろよ。
