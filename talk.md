# ちょっとマニアックな○○コマンドの使い方



<details>
<summary>だれこれ</summary>

![pocke](https://cloud.githubusercontent.com/assets/4361134/26518086/425140a4-42e3-11e7-86c3-885af2b5c802.png)

- Pocke
- Actcat inc. / Engineer
- Rubyist, Vimmer, Arch Linux :heart:

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


</details>

<details>
<summary>rwww</summary>


</details>

<details>
<summary>sl</summary>


</details>


<details>
<summary>git</summary>


</details>


</details>
