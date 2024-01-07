---
title: "オライリー本を形式Kindle app(Mac, iPad)で読む方法"
emoji: "👽"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["kindle", "epub", "mobi"]
published: true
---

この記事では、epubとpdfをKindle app(Mac, iPad)で読めるようにする方法を書いていきます。
- 各端末にKindle appがインストールされていることが前提です。
  - [Kindle for Mac](https://www.amazon.com/gp/browse.html%3Fnode=16571048011&ref=kcp_fd_hz) or [homebrew](https://github.com/Homebrew/homebrew-cask/blob/HEAD/Casks/kindle.rb)
  - Kindle for iPadは、App storeからインストール
- この記事では、[Send to Kindle](https://www.amazon.co.jp/gp/help/customer/display.html?nodeId=G7NECT4B4ZWHQ8WV)の方法は使用しません。
  - 最大50MBまで送信が可能ですが、Gmailを使用している場合は25MBまでしかファイル添付できないことと、仮に送れるようにするにしても手間が多いためです。

# 電子書籍購入
オライリージャパンではkindle版の発売がほぼ無く、代わりにオライリージャパンで電子書籍版を購入することができます。
https://www.oreilly.co.jp/index.shtml

購入すると、epubとpdfの形式でダウンロードすることができます。

# epubをKindle appで読めるようにする
:::message
2024/01/07 追記
現在は、Webから[Send to Kindle](https://www.amazon.co.jp/sendtokindle)ができるようになっています。
:::

Send to Kindleで受け付けている形式でepubがないことから、epub を Kindle app で読めるようにするためには、Kindle 形式にする必要があります。
ここでは、mobiファイルを用意します。
https://www.amazon.co.jp/gp/help/customer/display.html?nodeId=G5WYD9SAF7PGXRNA

## mobiファイルを用意する
1. 必要なappを用意
[kindle previewer](https://www.amazon.com/gp/feature.html?ie=UTF8&docId=1003018611) or [homebrew](https://github.com/Homebrew/homebrew-cask/blob/HEAD/Casks/kindle-previewer.rb)

2. kindle previewerでepubをmobiへ変換する
[本を開く]でepubファイルを選択 > ファイル > エクスポート > ファイル形式で[本(.mobi)]を選択し、任意の場所に保存します。

### Kindle for Mac
:::message alert
2024/01/07 追記
以下の情報は、現在のKindle for Macが出る前のkindle(Kindle Classic) の情報です。素直にSend to Kindleをお使いください
:::

Kindle for Macでは、app内でダウンロードしたkindle書籍は、以下のディレクトリに保存されます。
```shell
$ ls -la ~/Library/Application\ Support/Kindle/My\ Kindle\ Content/
```
このディレクトリに先ほどダウンロードした`***.mobi`をコピーします。

```shell
$ cp /path/to/***.mobi ~/Library/Application\ Support/Kindle/My\ Kindle\ Content/
```
この状態で、Kindle for Macを落として、再起動させると、`~/Library/Application\ Support/Kindle/My\ Kindle\ Content/`にコピーした `***.mobi`ファイルを初期化して、ディレクトリが作成されます。
これで、Kindle for Macから[ダウンロード済み]を見ると、購入した電子書籍が読めるようになります。

### Kindle for iPad
Kindle for iPadでは、Finder経由でKindle for iPadに直接`***.mobi`ファイルをコピーします。
1. MacとiPadをケーブルで直接接続します。
2. Finderを開き、iPad > ファイル > Kindle を選択します。
3. すると、ファイルをドラッグアンドドロップできるので、`***.mobi`ファイルをドラッグアンドドロップします。
4. この状態でKindle for iPadを再起動させると、LIBRARY > DOWNLOADED から購入した電子書籍が読めるようになります。

# pdf を Kindle app で読めるようにする

自分がオライリージャパンで買った本の中では、必ずepubとpdfは必ずダウンロードできるのですが、技術書典などで購入した本はpdfのみ配布されていることが多いです。
pdfからepub, mobi形式に変換してKindle appで読むことも可能ですが、pdf変換の際に日本語対応されておらず日本後が抜けていたり、mobi形式に変換してもメモができなかったりして、変換による情報の抜けや操作性が失われる可能性があるので、pdfのみしかファイルがない場合はそのままpdfで読むことにしています。

### Kindle for Mac
ライブラリ一覧画面で、ファイル > pdfをインポート で読めるようになります。

### Kindle for iPad
mobi形式と同じやり方で読めるようになります。
