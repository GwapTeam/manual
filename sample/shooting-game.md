# shooting-game手順書 


## 概要
JSのライブラリ学習がコンセプトです。
htmlへのライブラリのimport、createJSおよびゲームライブラリ全般に共通する特有な動作の第一歩としての学習になります。
_最下部にextra完成時のコメントつきjsがあります。_

## 注意
改行は手順書での指定はないためよしなにしてください。
jsの書き方は基本的に手順書どおりですが、わからない点があれば[開発マニュアル](https://github.com/GwapTeam/manual)を参考にしてください。

### 学習ポイント
* ライブラリの導入
    * html内にライブラリjsのpathを記述
* new演算子の学習(インスタンス)
* FPSの学習
* Tickイベント
    * 1flame毎に呼ばれるイベント
* x軸, y軸の学習


## complete
### ファイル概要
- 生徒編集あり
    - shooting-game.html
    - js/shooting-game.js

- 生徒編集なし
    - css/shooting-game.css
    - js/createjs-min.js

- 取り込み済み
    - css/shooting-game.css

- 生徒取り込み
    - js/createjs-min.js
    - js/shooting-game.js

- 完成時ファイル
    - complete-shooting-game.html
    - js/complete-shooting-game.js


### 手順

1. jsの取り込み
    - `shooting-game.html`をsublimeで開く
    - `body`タグ内に`canvas`タグを入力(canvas追加とjs取り込み)
      ```html
        <canvas id="canvas" width="960" height="540"></canvas>
        <script src="js/createjs-min.js"></script>
        <script src="js/shooting-game.js"></script>
      ```

2. Stageと自機を表示
    - `js/shooting-game.js`をsublimeで開く
    - 下記を入力
      ```javascript
        window.onload = function() {
            var stage = new createjs.Stage("canvas");
            var STAGE_W = 1000;
            var STAGE_H = 500;

            var bg = new createjs.Shape();
            bg.graphics.beginFill("green").drawRect(0, 0, STAGE_W, STAGE_H);
            stage.addChild(bg);

            var player = new createjs.Shape();
            player.graphics.beginFill("blue").moveTo(5, 0).lineTo(-20, 10).lineTo(-20, -10);
            stage.addChild(player);

            stage.update();
        }
      ```
        - `window.onload = function() {}`
            - windowの読みこみ完了後の処理として登録
        - `var stage = new createjs.Stage("canvas");`
            - idがcanvasの物を引数とし、createjsのStageインスタンスを生成
        - `var STAGE_W = 1000; var STAGE_H = 500;`
            - ステージのサイズを指定(`canvas`タグのwidth heigthに合わせる)
        - `var bg = new createjs.Shape();`
            - 背景用Stageインスタンスを生成
        - `bg.graphics.beginFill("green").drawRect(0, 0, STAGE_W, STAGE_H);`
            - 配置場所,サイズ、背景色を指定
        - `stage.addChild(bg);`
            - ステージの子要素として背景(bg)を追加
        - `var player = new createjs.Shape();`
            - 自機の作成
        - `player.graphics.beginFill("blue").moveTo(5, 0).lineTo(-20, 10).lineTo(-20, -10);`
            - 自機の形、色を指定
        -  `stage.addChild(player);`
            -  ステージの子要素として自機(player)を追加
    - htmlを確認😏
        - 自機は配置座標を決めて来ないため、初期値のx=0,y=0にいます。
        - 左上を良く見るとうっすら青色が見えます。
3. Tickイベントの登録、同時に敵の表示、自機の移動
    - `var STAGE_H = 500;`の下部に下記を追加(flameのカウント)
      ```javascript
        var count = 0;
        var enemyList = [];
      ```
      ```javascript
        // 追加後の変数宣言部分
        var stage = new createjs.Stage("canvas");
        var STAGE_W = 1000;
        var STAGE_H = 500;
        var count = 0;      // <- 追加
        var enemyList = []; // <- 追加
      ```
    - htmlを確認😉
    - 既存の`stage.update();`を削除
        - 下に説明されるtickイベントで移動されます。
    - `stage.addChild(player);`の下部に下記を追加(Tickイベントの登録)
      ```javascript
        createjs.Ticker.setFPS(60);
        createjs.Ticker.addEventListener("tick", handleTick);

        function handleTick() {
            player.x = stage.mouseX;
            player.y = stage.mouseY;
            count += 1;

            if (count % 120 == 0) {
                var enemy = new createjs.Shape();
                enemy.graphics.beginFill("red").moveTo(-5, 0).lineTo(10, +5).lineTo(10, -5).closePath();
                enemy.x = STAGE_W;
                enemy.y = STAGE_H * Math.random();
                stage.addChild(enemy);
                enemyList.push(enemy);
            }
            stage.update();
        }
      ```
      ```javascript
        // コメント付き　　//
        
        // FPSを60に指定
        createjs.Ticker.setFPS(60);
        // tickEventとしてhandleTick関数を登録
        createjs.Ticker.addEventListener("tick", handleTick);

        // handleTick関数を定義
        function handleTick() {
            // 自機(player)をマウスの座標に合わせる。
            player.x = stage.mouseX;
            player.y = stage.mouseY;
            // flame count をインクリメント
            count ++;

            // 2秒に一回 true
            if (count % 120 == 0) {
                // 敵機のインスタンス作成
                var enemy = new createjs.Shape();
                // 敵機の色とサイズを指定
                enemy.graphics.beginFill("red").moveTo(-5, 0).lineTo(10, +5).lineTo(10, -5).closePath();
                // 敵機をステージの右端に配置
                enemy.x = STAGE_W;
                // 敵機をステージの高さランダムに配置
                enemy.y = STAGE_H * Math.random();
                // ステージに敵機を追加
                stage.addChild(enemy);
                // 敵機の配列に追加 当たり判定の時使う
                enemyList.push(enemy);
            }
            // ステージの更新(移動後)
            stage.update();
        }
      ```
    - htmlを確認😆
        - 2秒ごとに画面右端に敵機が見えるか確認
4. 銃弾の発射と銃弾・敵機の移動処理追加
    - `js/shooting-game.js`をsublimeで開く
    - `var enemyList = [];`の下部に下記を追加(flameのカウント)
        ```javascript
        var bulletList = [];
        ```
        ```javascript
        // 追加後の変数宣言部分
        var stage = new createjs.Stage("canvas");
        var STAGE_W = 1000;
        var STAGE_H = 500;
        var count = 0;
        var enemyList = [];
        var bulletList = []; // <- 追加
        ```
    - handleTick関数の下にshot関数を追加
        ```javascript
        function shot() {
            var bullet = new createjs.Shape();
            bullet.graphics.beginFill("white").drawCircle(0, 0, 3);
            bullet.x = player.x;
            bullet.y = player.y;
            stage.addChild(bullet);
            bulletList.push(bullet);
        }
        
        stage.addEventListener("click", handleClick);
        ```
        ```javascript
        // コメント付き //
        
        // shot関数定義(銃弾発射)
        function shot() {
            // 銃弾のインスタンス生成
            var bullet = new createjs.Shape();
            // 銃弾の形と色を指定
            bullet.graphics.beginFill("white").drawCircle(0, 0, 3);
            // 座標を自機(player)の座標に指定
            bullet.x = player.x;
            bullet.y = player.y;
            // ステージの子要素に追加
            stage.addChild(bullet);
            // 銃弾の一覧に追加 (当たり判定処理で使用)
            bulletList.push(bullet);
        }
        
        // stageインスタンスのclickEventにshot関数を追加
        stage.addEventListener("click", shot);
        ```
    - handleTick関数の中の`stage.update();`の上に下記を追加
        ```javascript
        for (var i = 0; i < bulletList.length; i++) {
            bulletList[i].x += 10;
        }
        ```
        ```javascript
        // 順番確認用 //
                enemyList.push(enemy);
            }

            for (var i = 0; i < enemyList.length; i++) {
                enemyList[i].x -= 2;
            }

            // bulletListのx座標全てに10インクリメント
            for (var i = 0; i < bulletList.length; i++) {
                bulletList[i].x += 10;
            }

            stage.update();
        }
        ```
    - htmlを確認😅
        - クリックして銃弾が発射される
        - 敵機が動く

5. 当たり判定の追加
    - `js/shooting-game.js`をsublimeで開く
    - handleTick関数の中の`stage.update();`の上に下記を追加
        ```javascript
        for (var j = 0; j < enemyList.length; j++) {
            for (var i = 0; i < bulletList.length; i++) {
                var bullet = bulletList[i];
                var enemy = enemyList[j];
                var local = bullet.localToLocal(0, 0, enemy);

                if (enemy.hitTest(local.x, local.y) == true) {
                    stage.removeChild(enemyList[j]);
                    enemyList.splice(j, 1);
                }
            }
        }
        ```
        ```javascript
        // コメント付き //

        for (var j = 0; j < enemyList.length; j++) {
            for (var i = 0; i < bulletList.length; i++) {
                var bullet = bulletList[i];
                var enemy = enemyList[j];
                // *1
                var local = bullet.localToLocal(0, 0, enemy);
                // *1
                // enamy.x == bullet.xとかにするとFPS的にできません。
                if (enemy.hitTest(local.x, local.y) == true) {
                    //　ステージから削除
                    stage.removeChild(enemyList[j]);
                    // 敵配列から削除
                    enemyList.splice(j, 1);
                }
            }
        }
        ```
        - *1 [参考サイト](https://ics.media/tutorial-createjs/hittest.html)

    - htmlを確認😅
        - 銃弾撃って敵に当たったとき消えれば成功

**complete終了**

---


## extra

### 概要
- 自動発射の追加
- 終了判定および処理の追加
- スコアの追加
### ファイル概要
- 生徒編集あり
    - js/shooting-game.js

- 生徒編集なし
    - shooting-game.html
    - css/shooting-game.css
    - js/createjs-min.js

- 取り込み済み
    - css/shooting-game.css
    - js/createjs-min.js
    - js/shooting-game.js

- 完成時ファイル
    - extra-shooting-game.html
    - js/extra-shooting-game.js


### 手順

1. 自動発射の追加
    - `js/shooting-game.js`をsublimeで開く
    - `handleTick`関数内 `enemyList.push(enemy); }`下部(32行目あたり)に下記を追加
        ```javascript
        if (count % 60 == 0) {
            shot()
        }
        ```
        - 60flame(１秒)に一回銃弾を撃つ　
    - htmlを確認😇

2. 終了判定および処理の追加
    - `js/shooting-game.js`をsublimeで開く
    - `stage.addEventListener("click", shot);`下部(73行目あたり)に下記を追加
        ```javascript
        function gameOver() {
            createjs.Ticker.removeAllEventListeners();
            stage.removeAllEventListeners();

            var text = new createjs.Text("Game Over", "48px sans-serif", "white");
            text.textAlign = "center";
            text.x = STAGE_W / 2;
            text.y = STAGE_H / 2;
            stage.addChild(text);
        }
        ```
        ```javascript
        // コメント付き //
        
        // gameOver関数の宣言
        function gameOver() {
            // Tickerイベントの削除(画面更新が停止)
            createjs.Ticker.removeAllEventListeners();
            // stageのイベントの削除(クリックイベントの削除　)
            stage.removeAllEventListeners();

            // GameOverとScoreの表示用インスタンス生成
            var text = new createjs.Text("Game Over", "48px sans-serif", "white");
            // scoreのStyle指定(中央ぞろえ)
            text.textAlign = "center";
            // Scoreの表示用インスタンスの座標指定(中央)
            text.x = STAGE_W / 2;
            text.y = STAGE_H / 2;
            // stageの子要素として追加
            stage.addChild(text);
        }
        ```
        
    - `for (var i = 0; i < enemyList.length; i++) {　enemyList[i].x -= 2;`下部(３９行目あたり)に下記を追加
        ```javascript
            if (enemyList[i].x < 1) {
                gameOver();
            }
        ```
        ```javascript
        // 順番確認用 //
        for (var i = 0; i < enemyList.length; i++) {
            enemyList[i].x -= 2;
            if (enemyList[i].x < 1) {
                gameOver();
            }
        }
        ```
        - 敵が画面左端に到達したらゲームオーバーになる処理
    - htmlを確認😕
        - 敵が左端に到達した時にGameOverと表示されるか確認
        
3. スコアの追加
    - `js/shooting-game.js`をsublimeで開く
    - `var enemyList = [];`の下部に下記を追加(flameのカウント)
        ```javascript
        var score = [];
        ```
        ```javascript
        // 追加後の変数宣言部分
        var stage = new createjs.Stage("canvas");
        var STAGE_W = 1000;
        var STAGE_H = 500;
        var count = 0;
        var enemyList = [];
        var bulletList = [];
        var score = 0; // <- 追加
        ```
    - `stage.addChild(player);`の下部(17行目あたり)に下記を追加
        ```javascript
        var scoreText = new createjs.Text("0", "24px sans-serif", "white");
        stage.addChild(scoreText);
        ```
        - 初期値として0のtextをstageの子要素として追加
    - `handleTick`関数内の当たり判定処理部分`enemyList.splice(j, 1);`の下部に下記を追加
        ```
        score += 100;
        scoreText.text = score;
        ```
        ```javascript
        // 順番確認用 //
                    if (enemy.hitTest(local.x, local.y) == true) {
                        stage.removeChild(enemyList[j]);
                        enemyList.splice(j, 1);

                        score += 100; // <- 追加
                        scoreText.text = score;// <- 追加
                    }
                }
            }

            stage.update();
        }
        ```

## 終わり
お疲れ様です。
