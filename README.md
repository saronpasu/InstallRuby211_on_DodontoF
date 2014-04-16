## どどんとふを Ruby 2.1.1 で動かす方法

さくらのレンタルサーバ（スタンダードプラン）で、
Ruby 2.1.1 でどどんとふを動かしてみるよ！

---
## 環境

- さくらレンタルサーバ でやりました
- スタンダードプラン 以上は必要です
- SSH 接続でやりました
- Ruby はソースからビルドしました
- どどんとふ はインストール済みです

---
## やり方

1) SSH 接続します

```shell
$ ssh your_id@your_domain.sakura.ne.jp         #(your_id にあなたのアカウント、 your_domain にあなたのドメインを入力します)
your_id@your_domain.sakura.ne.jp's password:   #(パスワードを入力します)
```

2) ホームディレクトリに local/src ディレクトリを作成します

```shell
$ cd ~/
$ mkdir -p local/src
```

3) インストールに必要なコマンドが実行可能か確認しましょう。

```shell
$ which wget
#=> /usr/local/bin/wget
$ which tar
#=> /usr/local/bin/tar
$ which vim
#=> /usr/local/bin/vim
```

4) Ruby 2.1.1 をダウンロードして、展開します。

```shell
$ cd ~/local/src
$ wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.1.tar.gz
$ tar zxf ruby-2.1.1.tar.gz
```

5) Ruby 2.1.1 を local にインストールします。

```shell
$ cd ruby-2.1.1
$ ./configure --prefix=$HOME/local --with-opt-dir=$HOME/local
$ make
$ make install
```

6) Ruby が local にインストールされているか確認しましょう。

```shell
$ ~/local/bin/ruby -v
#=> ruby 2.1.1p76 (2014-02-24 revision 45161) [x86_64-freebsd9.1]
```

7) vim 等で DodontoFServer.rb の１行目を書き換えます。(your_id の部分はあなたのアカウントに変更して下さい)

```diff
-#!/usr/local/bin/ruby -Ku
+#/home/your_id/local/bin/ruby -Ku
```

8) どどんとふが正常に稼働しているかどうか確認しましょう。

   もし、正常に稼働していない場合は DodontoFServer.rb の１行目を元に戻して下さい。

9) これで、あなたのどどんとふも最新版の Ruby で快適に動作しますね！

---
参考: [さくらのレンタルサーバに Ruby 1.9.3 と gem をインストール](http://tech.tmd45.jp/entry/2013/07/03/182414)

Author [saronpasu](https://twitter.com/saronpasu)
