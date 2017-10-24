# QUIZ GAME手順書
## 使用ファイル
### 編集あり
- quiz-start.html
- quiz-question.html
- quiz-result.html
- js/quiz.js
- js/quiz-result.js
- css/quiz.css
---
## 概要（メモです）
quiz-question.htmlにおいて
- bodyタグ に   [onload="updateQuestion();"]を追記
- buttonタグに  [onclick="questionJudge(1)"]を追記
- buttonタグに  [onclick="questionJudge(0)"]を追記

quiz-result.htmlにおいて
bodyタグに　[onload="result()"]を追記

quiz.jsにおいて
全てを記述

quiz-result.jsにおいて
全てを記述


--- <b>extra問題</b> ---

完成したquesiton-result.htnlにおいて
１つ目のthタグ、正解数の下に [`<th>不正回数</th>`]と[`<th>正答率</th>`]を追記
２つ目のthタグ、"score"の下に [`<td id="missCount"></td>`]と`<td id="percentage"></td>`を追記

quiz.cssにおいて
a,    border-radius: 8px;


---
## 手順

1.現状の確認
- **quiz-start.html**をchromeで開く
- スタートボタンを押す
    - quiz-question.htmlに移動するが問題文が出ていない
      - 解消するためにJSを記述する↓ 
    - YES/NOボタンを押しても反応がない
        

---

2.JS,HTMLの記述
- **quiz.js**をsublime_textで開く
  - １～８行目に下記を入力（配列）
 
         1|var quizzes = [
         2|    "テトリスを作ったのは日本人である",
         3|    "１円玉の直径は2cmである",
         4|    "塩はカロリー0である",
         5|    "レモンはミカン科の果物である",
         6|    "パンとご飯を同じ分量だけ食べた時、消化が早いのはパンである",
         7|    "ドライブスルーは馬で入っても注文できる"
         8|];  //問題のリスト

  - ９～１２行目に下記を入力（変数）

         9|var answerList   = [0, 1, 1, 1, 0, 1];   //0の時NOを選ぶと正解、1の時YESを選ぶと正解
        10|var score        = 0;                    //正解数
        11|var index        = 0;                    //現在の回答数
        12|var question     =                 document.getElementById("question");

  - １４～１６行目に下記を入力
 
         14|function updateQuestion() {
         15|    question.innerText = "問題" + (index + 1) + ":" + quizzes[index];
         16|}

 - **quiz.html**をsublime_textで開く
   -  bodyタグ内に下記を入力

           14|onload="updateQuestion();"
    
 - ブラウザに戻り、変更を確認(F5キー) 
    - 問題文が反映されている
    - YES/NOボタンはまだ動かない
      - これを解消するためにJSを書く↓

 - **quiz.js**へ移動
    - １８～３５行目に下記を入力

           18|function questionJudge(check) {
           19|
           20|    if (check == answerList[index]) {
           21|    alert("正解"+ (index + 1) + "問目終了。");
           22|    score++;
           23|    } else {
           24|        alert("不正解"+ (index + 1) + "問目終了。");
           25|    }
           26|          
           27|    if(index >= quizzes.length - 1) {
           28|        localStorage.setItem("score", score);
           29|        localStorage.setItem("quizCount", quizzes.length);
           30|        location.href="quiz-result-complete .html";
           31|    }
           32|
           33|    index++;
           34|    updateQuestion();
           35|}
           
 - **quiz_html**へ移動
   - buttonタグ内に下記のonclickを追記
           
           23| <button
           24|     onclick="questionJudge(1);"
           25| >
           
           28| <button
           29|     onclick="questionJudge(0);"
           30| >
 
 - ブラウザに戻り、挙動を確認する
     - YES/NOボタンは正常動作する
     - quiz_result.htmlに結果が出ていない
       - 修正のため、記述↓

 - **quiz_result.js**をsublime_textで開く
     - １行目～４行目に下記を入力
     
              1|function result() {
              2|    var score  = localStorage.getItem("score");
              3|    document.getElementById("score").innerText = score;
              4|}

 - **quiz_result.html**をsublime_textで開く
     - bodyタグ内に下記を入力
     
             13|    onload="result();"
             
 - ブラウザに戻り、挙動を確認
     - quiz_start.htmlからやり直し
       - 実際に問題を解き、自分の正解数とresultで表示された正解数が一致しているか確認する
     　　
---

## extra手順
1.現状の確認
- 完成したhtmlを開き、動作を確認する
  - **quiz-start.html**をchromeで開く
    - 結果画面まで行く

2.結果画面項目の追加
- 結果画面の項目を増やすため、**quiz_result.html**をsublime_textで開く
　　- ２１、２２行目に`<th>`タグを追記
　　
  
         21|<th>不正解数</th>
         22|<th>正答率</th>
         
   - ２８、２９行目に`<td>`タグを追記


         28|<td id="missCount"></td>
         29|<td id="percentage"></td>

   - これで項目は追加された
     - まだ数字は出ていないのでJSに追記↓

- **quiz-result.js**をsublime_textで開く
   - ３～５行目に下記を入力
 
          3|var quizCount = localStorage.getItem("quizCount");
          4|var missCount = quizCount - score;
          5|var percentage = Math.round(score/quizCount * 100);
          
   - ７、８行目に下記を入力(行頭は３～５行目に合わせる)
 
          7|document.getElementById("missCount").innerText = missCount;
          8|document.getElementById("percentage").innerText = percentage + "%";

- ブラウザに戻り、動作を確認する
  - quiz_result.htmlにて不正解数と正答率の項目が増えている

3.ボタンの角を丸くする
- **quiz.css**をsublime_textで開く
  - ２２行目に下記を追記

        22|border-radius: 8px;
- ブラウザに戻り、cssが反映されているか確認する
  - ボタンの角が丸くなっている
 
