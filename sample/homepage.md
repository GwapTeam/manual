# homepage手順書 

### 注意
今回は生徒が比較的自由にcssを触るため、完成系が自由です。
サンプルとして
* complete_homepage_1.css extra_homepage_1.css
* complete_homepage_2.css extra_homepage_2.css

を用意しています。
それぞれ
* complete_homepage.html（cssリンクを変更すればデザインが変わります）
* extra_homepage.html（cssリンクを変更すればデザインが変わります）

にて管理されています。

_**生徒が実際に取り込むcssは１つなので注意してください。
各ページへのリンク`<a>タグ`の対象先は本番環境のディレクトリに合わせてください**_


## **complete**
### 編集あり
- homepage.html
- css/homepage.css
### 編集なし
- js/homepage.js

### 取り込み
- img/{使用画像}
- js/homepage.js

## 手順

1. htmlでタグの学習
    - `homepage.html`をsublimeで開く
    - 10行目に下記を入力(`<body>`の2行下)
      ```html
      <!DOCTYPE html>
      <html lang="ja">
      <head>
          <title>ゲーム紹介ホームページ</title>
      </head>
      
      <body>
          <nav>
              <div>
                  <a href="#header">My Homepage</a>
                  <button onclick=onMenuButtonClick()>メニュー</button>
              </div> 
              <ul>
                  <li>
                      <a href="#easy-quiz">簡単クイズゲーム</a>
                  </li>
                  <li>
                      <a href="#typing">タイピングゲーム</a>
                  </li>
                  <li>
                      <a href="#quiz">クイズゲーム</a>
                  </li>
                  <li>
                      <a href="#early-press">早押しゲーム</a>
                  </li>
                  <li>
                      <a href="#about">自己紹介</a>
                  </li>
              </ul>
          </nav>
      </body>
      </html>
      ```
    - htmlを確認😏
    - `</nav>`に下記を入力（headerを記述）
      ```html
      <header id="header">
          <h1>ゲーム倉庫</h1>
          <p><b>ようこそ！ 学研教室に通って僕が作ったゲーム紹介ホームページです！</b></p>
      </header>
      ```
    - htmlを確認😉
    - `</header>`下記に入力(sectionを記述)
      ```html
      <section id="easy-quiz">
          <h1>簡単クイズゲーム</h1>
          <p>HTMLについてのクイズ問題だよ！</p>
          <a href="../easy-quiz/easy-quiz.html">Let Play!</a>
      </section>

      <section id="typing">
          <h1>タイピングゲーム</h1>
          <p>食べ物のタイピングゲームだよ！</p>
          <a href="../typing-game/complete-typing.html">Let Play!</a>
      </section>

      <section id="quiz">
          <h1>クイズゲーム</h1>
          <p>食べ物のクイズゲームだよ！</p>
          <a href="../quiz/complete-quiz-start.html">Let Play!</a>
      </section>

      <section id="early-press">
          <h1>早押しゲーム</h1>
          <p>1から30までの数字の早押しゲームだよ！</p>
          <a href="../early-press/early-press.html">Let Play!</a>
      </section>
      ```
    - htmlを確認😆
    - `</section>`下記に入力(自己紹介ページを表示)
      ```html
      <iframe id="about" src="../self-introduction/complete-self-introduction.html"></iframe>
      ```
    - htmlを確認😅
    - `<iframe>`に下記に入力(事前に用意してある特別js)
      ```html
      <script src="js/homepage.js"></script>
      ```
      
* ひと休憩 クッソダサいページが確認できてます？
* ここでのstyleの学習は前述の通り生徒が自由に触ってくから要検討

3. styleの学習
    - `homepage.html`をsublimeで開く
    - `<head>`内`<title>`の下に入力(css fileへのリンクを記述)
      ```html
      <link href="css/homepage.css" rel="stylesheet">
      ```
      挿入後のhead(sample)
      ```html
      <head>
          <title>ゲーム紹介ホームページ</title>
          <link href="css/complete_homepage_2.css" rel="stylesheet">
      </head>
      ```
    - `homepage.css`をsublimeで開く
    - 下記を入力（基本的なレイアウト）
        ```html
        body {
            margin: 0;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
        }

        nav > ul {
            list-style-type: none;
            display: flex;
        }

        header {
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100vh;
            text-align: center;
        }
        
        section {
            display: flex;
            flex-direction: column;
            justify-content: center;
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
        }
        ```
        - [flexboxについて](https://qiita.com/hashrock/items/939684b9207dbab1d59e)
        - [flexboxについて2](https://developer.mozilla.org/ja/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)
            - 難しいと思うんで杉山に聞いてください
    - htmlを確認😤
    - `header`タグ内に下記を入力（画像を追加）
        ```html
        background: url(../img/好きな画像を選んでね);
        ```
        ```html
        /*挿入後header*/
        header {
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100vh;
            text-align: center;
            background: url(../img/bg_11);
        }
        ```
    - 下記を入力（id毎に画像を追加）
        ```html
        #easy-quiz {
            background-image: url(../img/bg_1);
        }

        #typing {
            background-image: url(../img/bg_2);
        }

        #quiz {
            background-image: url(../img/bg_3);
        }

        #early-press {
            background-image: url(../img/bg_4);
        }
        ```
    - htmlを確認😇
    - 下記を入力（ヘッダーボタンと通常のボタンのスタイルと自己紹介ページの拡大、）
        ```  
        iframe {
            width: 100vw;
            height: 100vh;
            border: none;
        }

        a {
            color: orange;
            text-decoration: none;
        }

        nav a {
            margin: 0 8px;
        }

        section a {
            padding: 8px 20px;
            border-radius: 30px;
        }
        ```
    - htmlを確認😇

* この時点である程度きったねえhtmlができてると思います
* こっからは生徒が自由にもっと綺麗にしていきます。
* 教材で成果物を縛ることなく、どうしたいか今まで学習した範囲から生徒が考え実行させるために、講師がサポートしてあげる教材にしましょう！（学研からの無茶振り）

* サンプルとしてcss/complete-homepage_1.cssとcss/complete-homepage_2.cssがあります。

* 実装例
    * `body`にfontと背景色を指定
        ```html
        font-family: 自由;

        ```
        ```html
        /*挿入後header*/
         body {
            margin: 0;
            font-family: fantasy;
            background-color: darkslategray;
         }
        ```
    
    * `nav`に背景色を指定
        ```html
        background-color: 自由;

        ```
        ```html
        /*挿入後header*/
         body {
             background-color: crimson;
         }
        ```
    * `h1` `p`に色を指定
        ```html
         h1,
         p {
            background: rgba(20,20,20,0.5);
            color: white;
         }
        ```
    * `section`に色々追加　
        ```html
         section {
            margin: 20px;
            padding: 40px;
            align-items: flex-start;
            height: 300px;
         }
        ```
    * 2の倍数の`section`を右寄せにするよ
        ```html
        section:nth-child(2n) {
            align-items: flex-end;
        }
        ```
    * `nav`タグの`a`タグの色を追加
        ```html
         nav a {
             color: white;
         }
        ```
    * `section`タグの`a`タグのfontの色とfontの太さを追加
        ```html
         section a {
            background: orange;
            color: white;
            font-weight: bold;
         }
        ```

---

## **extra**
### 概要
ナビゲーションをスマホ対応にします
### 編集あり
- homepage.html
- css/homepage.css
### 編集なし

## 手順
2. styleの学習
    - `homepage.html`をsublimeで開く
    - `head`タグ内に下記を追加
        ```html
        <meta name="viewport" content="width=device-width">
        ```
        ```html
        <!-- 追加後のhead -->
        <head>
            <title>ゲーム紹介ホームページ</title>
            <meta name="viewport" content="width=device-width">
            <link href="css/extra_homepage_1.css" rel="stylesheet">
        </head>
        ```
        

    - chromeのdebug modeでスマホにし、htmlを確認(´・∀・｀)
    - `body` > `nav` > `div`に`button`タグを追加
        ```html
        <button onclick=onMenuButtonClick()>メニュー</button>
      ```
      挿入後の`nav`タグ
      ```html
        <nav>
            <div>
                <a href="#header">My Homepage</a>
                <button onclick=onMenuButtonClick()>メニュー</button>
            </div>
            <ul>
                <li>
                    <a href="#easy-quiz">簡単クイズゲーム</a>
                </li>
                <li>
                    <a href="#typing">タイピングゲーム</a>
                </li>
                <li>
                    <a href="#quiz">クイズゲーム</a>
                </li>
                <li>
                    <a href="#early-press">早押しゲーム</a>
                </li>
                <li>
                    <a href="#about">自己紹介</a>
                </li>
            </ul>
        </nav>
      ```
    - `</body>`直前にscriptを記述
      ```html
        <script>
            var menuIsVisible = false;
            var nav = document.getElementById("nav");
            function onMenuButtonClick() {
                if (menuIsVisible == true) {
                    nav.children[1].style.display = "none"
                    menuIsVisible = false;
                } else {
                    nav.children[1].style.display = "block"
                    menuIsVisible = true;
                }
            }
        </script>
        ```
    - css/homepage.cssに下記を追加
        ```css
        nav button {
            display: none;
        }

        @media (max-width: 767px) {
            nav button {
                display: inline-block;
            }
            nav {
                min-height: 60px;
                flex-direction: column;
                justify-content: center;
            }
            nav > ul {
                display: none;
                flex-direction: column;
            }
        }
        ```
    - htmlを確認(´\^∀\^｀)

## 終わり
疲れましたね
お疲れ様です。
質問あったらください
