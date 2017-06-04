# ちょっとマニアックな○○コマンドの使い方



<details>
<summary>だれこれ</summary>

![pocke](https://cloud.githubusercontent.com/assets/4361134/26518086/425140a4-42e3-11e7-86c3-885af2b5c802.png)

- Pocke
- Actcat inc. / Engineer
- Rubyist, Vimmer, Arch Linux :heart:
- 趣味: OSS に Pull-Request を投げること: https://github.com/pulls?utf8=%E2%9C%93&q=is%3Amerged+is%3Apr+author%3Apocke+is%3Apublic+-user%3Apocke
- Twitter: [`@p_ck_`](https://twitter.com/p_ck_)
- GitHub: [`@pocke`](https://github.com/pocke)
- Facebook: [`@kwbr22`](https://facebook.com/kwbr22)

</details>


<details>
<summary>ちょっとマニアックな○○コマンドの使い方？</summary>


https://atnd.org/events/88084

![170527134245](https://cloud.githubusercontent.com/assets/4361134/26518051/7e228ddc-42e2-11e7-92d0-cff4adf2a27f.png)




</details>


<details>
<summary>マニアックなコマンド</summary>

- Eject コマンド以外にも、マニアックな使い方を秘めたコマンドはあるはず…
    - 色々なコマンドのマニアックな使い方を紹介します。




<details>
<summary>cat</summary>


  <details>
  <summary>普通の使い方</summary>

  cat コマンドは、ファイルの中身を表示するのに使います。

  ```bash
  $ cat /proc/version
  Linux version 4.10.13-1-ARCH (builduser@tobias) (gcc version 6.3.1 20170306 (GCC) ) #1 SMP PREEMPT Thu Apr 27 12:15:09 CEST 2017
  ```

  ファイルを指定しない場合は標準入力から読み込みます。

  ```bash
  $ cat | xsel --input --clipboard
  $ cat | pbcopy
  ```

  </details>
  <details>
  <summary>マニアックな使い方</summary>

  cat コマンドを使用すると、猫と対話することが可能です(DEMO)。

  ```bash
  $ cat
  にゃーん
  にゃーん
  みゃー
  みゃー
  # Ctrl + C で会話を終了できます
  ```

  </details>

</details>


<details>
<summary>ruby</summary>


  <details>
  <summary>普通の使い方</summary>

  Ruby プログラムを実行します。

  ```ruby
  # hello.rb
  def hello
    puts 'Hello, world!'
  end
  hello
  ```

  ```bash
  $ ruby hello.rb
  Hello, world!
  ```

  </details>

  <details>
  <summary>マニアックな使い方</summary>

  行単位の処理をいい感じにやります。
  例えば、空白区切りで数値が書かれているファイルから、行毎に最大値を出力したい場合。

  ```
  75 64 5 37 19 29 48 23 56 88
  20 74 3 57 37 95 10 67 1 23
  72 95 45 41 71 47 14 84 44 62
  98 10 13 47 85 57 25 98 12 62
  4 77 82 33 54 59 60 60 60 64
  58 13 36 35 22 99 23 18 58 87
  35 42 68 6 36 57 38 38 33 23
  36 65 60 82 95 76 41 69 23 34
  1 35 97 8 98 10 88 93 57 31
  97 7 54 43 18 59 83 45 45 25
  ```

  ```bash
  $ cat test.csv | ruby -pale '$_=$F.map(&:to_i).max'
  88
  95
  95
  98
  82
  99
  68
  95
  98
  97
  ```

  ### 解説

  Ruby のコマンドラインオプションが重要です。

  - `-p`: Ruby プログラムが while gets; end のループに囲まれているように動作します。また、`$_`に代入された文字列をループの終了時に出力します。
    - -> つまり、1行毎に処理します。
  - `-a`: オートスプリットモードが有効になります。各ループの先頭で、標準入力から読み込んだ文字列を、空白で区切って配列にしたものを`$F`に代入します。
  - `-l`: `-p`オプションで読み込む行から、行末の改行記号を外します。また、出力時に改行記号を追加します。
  - `-e`: この後に与えられた文字列をRubyのコードとして実行します。

  https://docs.ruby-lang.org/ja/latest/doc/spec=2frubycmd.html

  多分、perl でもだいたい同じことが出来ます。

  </details>

</details>

<details>
<summary>git-grep</summary>

  <details>
  <summary>普通の使い方</summary>

  `git grep hogehoge` とやると、Git管理下にあるファイルから`hogehoge`を検索します。便利。

  ```bash
  $ git grep ruby
  talk.md:<summary>ruby</summary>
  talk.md:  ```ruby
  talk.md:  $ ruby hello.rb
  talk.md:  $ cat test.csv | ruby -pale '$_=$F.map(&:to_i).max'
  talk.md:  https://docs.ruby-lang.org/ja/latest/doc/spec=2frubycmd.html
  ```

  また、いろんなオプションがあります。便利

  ```bash
  # -i 大文字小文字の違いを無視する。
  $ git grep -i ruby
  talk.md:- Rubyist, Vimmer, Arch Linux :heart:
  talk.md:<summary>ruby</summary>
  talk.md:  Ruby プログラムを実行します。
  talk.md:  ```ruby
  talk.md:  $ ruby hello.rb
  talk.md:  $ cat test.csv | ruby -pale '$_=$F.map(&:to_i).max'
  talk.md:  Ruby のコマンドラインオプションが重要です。
  talk.md:  - `-p`: Ruby プログラムが while gets; end のループに囲まれているように動作します。また、`$_`に代入された文字列をループの終了時に出力します。
  talk.md:  - `-e`: この後に与えられた文字列をRubyのコードとして実行します。
  talk.md:  https://docs.ruby-lang.org/ja/latest/doc/spec=2frubycmd.html
  talk.md:  $ git grep ruby
  talk.md:  talk.md:<summary>ruby</summary>
  talk.md:  talk.md:  ```ruby
  talk.md:  talk.md:  $ ruby hello.rb
  talk.md:  talk.md:  $ cat test.csv | ruby -pale '$_=$F.map(&:to_i).max'
  talk.md:  talk.md:  https://docs.ruby-lang.org/ja/latest/doc/spec=2frubycmd.html
  ```

  ```bash
  # -w 単語単位での検索をします。
  $ git grep -w a
  talk.md:  - `-a`: オートスプリットモードが有効になります。各ループの先頭で、標準入力から読み込んだ文字列を、空白で区切って配列にしたものを`$F`に代入します。
  ```

  </details>

  <details>
  <summary>マニアックな使い方</summary>

  ```zsh
  # In ~/.zshrc
  function /()
  {
    git grep $@
  }
  ```

  ```bash
  # これで検索できる
  $ / ruby

  # 勿論オプションも効く
  $ / -w ruby
  ```

  Vim っぽくて便利！
  </details>

</details>

<details>
<summary>www</summary>

  <details>
  <summary>普通の使い方</summary>

  これはコマンド自体がマニアックなので……
  </details>

  <details>
  <summary>マニアックな使い方</summary>

  https://github.com/pocke/www

  これだけでカレントディレクトリをサーブする HTTP サーバが立ち上がって便利(DEMO)。

  ```bash
  $ www
  ```

  - HTTP server
  - Open browser
  - random port

  要するに `pyhton -m http.server` の簡単便利バージョン
  </details>


</details>

<details>
<summary>sl</summary>


  <details>
  <summary>普通の使い方</summary>

  ターミナルに sl が走ります。便利(DEMO)

  ```bash
  $ sl
  ```

  オプションも色々あって楽しい(Let's `man sl`!)
  </details>

  <details>
  <summary>マニアックな使い方</summary>

  ## SL が走る原理

  - ターミナルに一定間隔でエスケープシーケンスを流している
    - つまり、一定間隔で文字列が流れているのをターミナルがいい感じに表示しているだけ


  ## おもしろ

  例えば、HTTP 越しに SL を走らせることが出来る。 https://github.com/pocke/sl-over-http

  DEMO

  # `curl https://e6ec6d92.ngrok.io` を実行！！！


  <details>

  <summary>-</summary>

  ## さらにマニアックな使い方

  See. [https://twitter.com/p_ck_](https://twitter.com/p_ck_)

  </details>


  </details>

</details>


<details>
<summary>git</summary>

  <details>
  <summary>普通の使い方</summary>

  ```bash
  $ git status
  $ git checkout hogehoge
  ```

  </details>

  <details>
  <summary>マニアックな使い方</summary>

  DEMO

  ```bash
  # git を沢山打っても期待した動作をして便利
  $ git git git git git git status
  ```

  See. https://github.com/pocke/dotfiles/blob/5673e4a08c67e771128ddb8425806232fc620afe/.gitconfig#L37
  </details>


</details>


</details>
