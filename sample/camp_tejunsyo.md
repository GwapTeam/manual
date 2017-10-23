<style type="text/css">
<!--
  h1 { text-align: center }
-->
</style>
# TYPING GAME 手順書

## 使用ファイル
- 編集有
    - typing_camp.html
    - css/typing_camp.css
    -js/typing_camp.js
- 編集無
    - css/typing_camp2.css
    - js/typing_camp2.js
    - img/background_camp.png

## 手順
1. HTMLファイルを開いて現状を確認
    - **typing_camp.html** を使用
    - HTMLファイルをchromeで開く
    ---
2. HTMLファイルにCSS,JSファイルを読み込む
    - **typing_camp.html** を使用
    - 16行目に下記を入力
    ```html
    16 | <link rel="stylesheet" type="text/css "href="css/typing_camp.css">
    ```
    - 58行目に下記を入力
    ```html
    58 | <script type="text/javascript" src="js/typing_camp.js"></script>
    ```
    - (変化ないけど)HTMLファイルを開き変更を確認←いらない?
    ---
3.jsファイルを編集してタイピングゲーム機能をつける
    - **typing_camp.js** を使用
    - 1~5行目に下記を入力
    ```js
    1 | var wordChars;
    2 | var messageArea;
    3 | var wordArea;
    4 | var list = ["A","B","C"];
    5 | var number = 0;
    ```
    - HTMLファイルを開き変更を確認
        - スタートボタンを押すと「A」と表示される

        ---
    - 7~16行目に下記を入力
    ```js
    7  | document.onkeydown = function (e) {
    8  |     var key;
    9  |     key = String.fromCharCode(e.keyCode);
    10 |
    11 |     if (wordChars == key) {
    12 |         number++;
    13 |         wordArea.textContent = list[number];
    14 |         wordChars = list[number];
    15 |     }
    16 | }
    ```
    - HTMLファイルを開き変更を確認
        - 正解時に次の文字に行く

        ---
    - 16~19行目に下記を入力
    ```js
    16 | if (number == list.length) {
    17 |     alert("終了しました！");
    18 |     number++;
    19 | }
    ```
    - HTMLファイルを開き変更を確認
        - 最後の文字を打った時に終了のアラートが出てくる

        ---
    - 6行目に下記を入力
    ```js
    6 | var time = 0;
    ```
    - 17~20行目のif文を下記に変更
    ```js
    17 | if (number == list.length) {
    18 |     clearInterval();   // 追加
    19 |     alert(time + "秒で終了しました！"); // 変更
    20 |     number++;
    21 | }
    ```
    - 23~25行目に下記を入力
    ```js
    23 | function countUp() {
    24 |     time++;
    25 | }
    ```
    - HTMLファイルを開き変更を確認
        - 時間計測機能を追加 アラートに表示される

        ---
    - 4行目の配列を下記に変更
    ```js
    4 | var list = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"];        
    ```
    - HTMLファイルを開き変更を確認
        - 問題がアルファベットすべてに
    ---
4. CSSファイルを編集してデザインを変更する
    - **typing_camp.css** を使用
    - 1~3行目に下記を追加
        - 画像は複数選択肢有

    ```css
    1 | #background{
    2 |     background-image: url(../img/background_camp.png);
    3 | }
    ```
    - HTMLファイルを開き変更を確認
        - 背景画像が追加されている

        ---
    - 1~3行目の#backgroundを下記に変更
        - 数値は調整可能(数値が小さいほどくもりが濃い)    
    ```css
    1 | #background{
    2 |     background-image: url(../img/background_camp.png);
    3 |     opacity: 0.5;   /* 追加 */
    4 | }
    ```
    - HTMLファイルを開き変更を確認
        - 背景画像にくもりがついて文字が見やすくなっている

        ---
    - 5~7行目に下記を入力
        - 色はなんでもOK
        - [色参考サイト](http://hogehoge.tk/webdev/color/)
    ```css
    5 | #word{
    6 |     color: Orange;
    7 | }
    ```
    - HTMLファイルを開き変更を確認
        - 問題文字色が変わってる

        ---
    - 8~10行目に下記を入力
        - 色はなんでもOK
        - [色参考サイト](http://hogehoge.tk/webdev/color/)
    ```css
    8  | .navbar{
    9  |     background-color: blue;
    10 |}
    ```
    - HTMLファイルを開き変更を確認
        - ナビゲーションバーの色が変わってる

