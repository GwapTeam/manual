# self-introduction手順書

## **complete**
### 編集あり
- self-introduction.html
### 編集なし

### 取り込み
- img/self.png

## 手順

1. 現状の確認
    - `self-introduction.html`をchromeで開く
    - 白紙を確認(´・ω・｀)

2. htmlでタグの学習
    - `self-introduction.html`をsublimeで開く
    - 10行目に下記を入力(`<body>`の2行下)
      ```html
      <h1>自己紹介</h1>
      ```
    - htmlを確認(´・∀・｀)
    - 11行目に下記を入力（画像を挿入）
      ```html
      <img src="img/self.png">
      ```
    - htmlを確認(´\^∀\^｀)
    - １2行目に下記を入力(抱負などを記述)
      ```html
      <p>今日はたくさん勉強します！</p>
      ```
    - htmlを確認（｀・ω・´）
    - 14, 15行目に下記を入力(名前を記述)
      ```html
      <h2>学研　太郎</h2>
      <h2>がっけん　たろう</h2>
      ```
    - htmlを確認（ ・\`ー・´）
    - 17 ~ 22行目に下記を入力(テーブル)
      ```html
      <table>
          <tr>
              <td>年齢</td>
              <td>10歳</td>
          </tr>
          <tr>
              <td>誕生日</td>
              <td>0月0日</td>
          </tr>
      </table>
      ```
    - htmlを確認 (｡+・\`ω・´)
    - `<table></table>`内にカラムを追加してゆく(生徒が好きなかず)
      ```html
      <tr>
          <td>hoge</td>
          <td>huga</td>
      </tr>
      ```
3. styleの学習
    - head内の下にstyleを追加
      ```html
          <style>
              body {
                  text-align: center;
              }
              table {
                  margin: 0 auto;
              }
          </style>
      ```
      挿入後のhead(sample)
      ```html
      <head>
          <title>自己紹介</title>
          <meta charset="UTF-8">
          <style>
              body {
                  text-align: center;
              }
              table {
                  margin: 0 auto;
              }
          </style>
      </head>
      ```
    - htmlを確認 (￣・ω・￣)

---

## **extra**
### 編集あり
- self-introduction.html
### 編集なし

## 手順
2. styleの学習
    - `self-introduction.html`をsublimeで開く
    - styleのbodyに下記を入力
      ```css
      font-family: monospace;
      background-color: aqua;
      ```
      挿入後の`body`
      ```css
      body {
          text-align: center;
          font-family: monospace;
          background-color: aqua;
      }
      ```
      * font-familyで好きなフォントの種類に変更させる。 - [参考サイト](https://w3g.jp/sample/css/font-family)
      * background-colorで背景色を確認　- [参考サイト](https://www.w3schools.com/tags/ref_colornames.asp)
    - htmlを確認(´・∀・｀)
    - styleのtableに下記を入力
      ```css
      font-size: 28px;
      text-align: left;
      ```
      挿入後の`table`
      ```css
      table {
          margin: 0 auto;
          font-size: 28px;
          text-align: left;
      }
      ```
      * font-sizeで文字サイズを変更
      * text-alignで文字の開始位置を指定
    - htmlを確認(´\^∀\^｀)
    - styleに下記を追加(h1)
      ```css
      h1 {
          color: white;
          font-size: 48px;
          width: fit-content;
          border-bottom: 1px solid red;
          margin: 20px auto;
      }
      ```
      * colorで文字の色を確認
      * widthで横幅を文字幅分に指定。(デフォルトだと100%になってしまいボーダーが長くなりすぎてしまう)
      * border-bottomで下線を指定。(1pxがサイズ, solidが種類, redが色) - [参考サイト](https://developer.mozilla.org/ja/docs/Web/CSS/border)
    - htmlを確認（｀・ω・´）
    - styleに下記を追加
      ```css
      h2 {
          font-size: 32px;
      }
      h2, h3 {
          margin: 3px;
      }
      p {
          font-size: 18px;
          color: blue;
      }
      ```
    - htmlを確認（｀・ω・´）
    - styleに下記を追加
      ```css"onmouseover"alert(1)"
      img {
          border: 1px solid blue;
          border-radius: 50%;
          transition: transform 0.3s ease;
      }
      img:hover {
          transition: transform 0.3s ease;
          transform: rotate(360deg);
      }
      ```
      * border-radiusでelementの角を丸くする
      * `:hover`でマウスがhoverした時のcssを記述
      * transformでアニメーションを作成
      * transitonでアニメーションの動きを制御 - [参考サイト](https://developer.mozilla.org/ja/docs/Web/CSS/transition)
    - htmlを確認（｀;ω;´）
