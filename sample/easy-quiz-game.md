<style>
    h1 { text-align: center }
    h2 { color: red; }
    h3 { color: orange; }
</style>
# easy-press-game 手順書
## 使用ファイル
- 完成ファイル
    - complete-easy-quiz.html
    - extra-easy-quiz.html
- 使用ファイル
    - easy-quiz.html
## 注意点
- quizの問題と解答は例です。
- インデントもふくめコピーペースト使えます
## 手順
***
### 通常問題
***

1. HTMLファイルを開いて現状を確認
    - **easy-quiz.html**をchromeで開く
        - 見出し「クイズゲーム」が表示される
2. scriptタグを記述
    - 12行目~14行目に下記を入力
    ``` html
    <script>
    
    </script>
    ```
3. alertを使用してクイズゲームを開始
    - 13行目に下記を入力
    ``` html
        alert("クイズゲーム開始！");
    ```
    - HTMLファイルを開き変更を確認
        - アラートが出てくる
4. promptを使用して問題を表示
    - 13行目の右端から2回改行
    - 15行目~16行目に下記を入力
    ``` html
        var ans;
        ans = prompt("見出しを表示するタグは？");
    ```
    - HTMLファイルを開き変更を確認
         - 入力ダイアログがでてくる
         - 入力しても何も起きない
5. ifを使用して正解判定の追加
    - 16行目の右端から2回改行
    - 18行目~20行目に下記を入力
    ``` html
        if (ans == "h1") {
            alert("正解！");
        }
    ```
    - HTMLファイルを開き変更を確認
        - 正解時 -> アラートで「正解！」
        - 不正解時 -> 何も起きない
6. elseを使用して不正解時の処理の追加
    - 20行目~23行目に下記を入力
    ``` html
        } else {
            alert("残念！");
            alert("正解は h1 でした！");
        }
    ```
    - HTMLファイルを開き変更を確認
        - 不正解時 -> アラートで「残念！」「正解は h1 でした！」
7. 問題の追加
    - 23行目の右端から2回改行
    - 25行目~31行目に下記を下記を入力
    ``` html
        ans = prompt("テーブルの列を表示するタグは？");
        if (ans == "tr") {
            alert("正解！");
        } else {
            alert("残念！");
            alert("正解は tr でした！");
        }
    ```
    - HTMLファイルを開き変更を確認
        - 1問目終了後、2問目が開始される
8. 問題の追加（上と同じ）
    - 31行目の右端から2回改行
    - 33行目~39行目に下記を入力
    ``` html
        ans = prompt("画像を表示するタグは？");
        if (ans == "img") {
            alert("正解！");
        } else {
            alert("残念！");
            alert("正解は img でした！");
        }
    ```
    - HTMLファイルを開き変更を確認
        - 2問目終了後、3問目が開始される

***
### 発展問題
***

1. buttonタグを追加
    - 10行目の右端から改行
    - 11行目に下記を入力
    ``` html
    <button>クイズ開始</button>
    ```
    - HTMlファイルを開き変更を確認
        - 見出しの下にボタンが追加される
        - アラート進めないとでない
2. ボタンクリックで問題開始
    - 13行目の右端を改行
    - 14行目~16行目に下記を入力
    ``` html
    function start(){
        
    }
    ```
    - 17行目~43行目を切り取り
    - 15行目に貼り付け
    ``` html
        function start(){
            alert("クイズゲーム開始！");

            var ans;
            ans = prompt("見出しを表示するタグは？");

            if (ans == "h1") {
                alert("正解！");
            } else {
                alert("残念！");
                alert("正解は h1 でした！");
            }

            ans = prompt("テーブルの列を表示するタグは？");
            if (ans == "tr") {
                alert("正解！");
            } else {
                alert("残念！");
                alert("正解は tr でした！");
            }

            ans = prompt("画像を表示するタグは？");
            if (ans == "img") {
                alert("正解！");
            } else {
                alert("残念！");
                alert("正解は img でした！");
            }
        }
    ```
    - 11行目に下記を入力（変更）
    ``` html
    <button onclick="start()">クイズ開始</button>
    ```
    - HTMLファイルを開き変更を確認
        - 表示されたボタンクリック後クイズ開始
3. 正解数を記録、表示
    - 17行目の右端から改行
    - 18行目に下記を入力
    ``` html
            var count = 0;
    ```
    - 22行目の右端から改行
    - 23行目に下記を下記を入力
    ``` html
                count++;
    ```
    - 31行目の右端から改行
    - 32行目に下記を下記を入力
    ``` html
                count++;
    ```
    - 40行目の右端から改行
    - 41行目に下記を下記を入力
    ``` html
                count++;
    ```
    - 45行目の右端から2回改行
    - 47行目~48行目に下記を入力
    ``` html
            alert(count + "問正解！");
            document.body.append(count + "問正解！");  
    ```
    - HTMLファイルを開き変更を確認
        - 3問終了後、ボタンの横、アラートに正解数が表示
4. 名前を記録、結果表示に追加表示
    - 18行目の右端から改行
    - 19行目に下記を入力
    ``` html
            var name;
    ```
    - 19行目の右端から2回改行
    - 21行目に下記を入力
    ``` html
            name = prompt("名前を教えてね！");
    ```
    - 50行目~51行目に下記を入力（変更）
    ``` html
            alert(name + "さんは" + count + "問正解！");
            document.body.append(name + "さんは" + count + "問正解！");
    ```
    - HTMLファイルを開き変更を確認
        - 結果表示時に名前も表示される
