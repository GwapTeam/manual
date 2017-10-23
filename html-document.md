HTML code style

ファイル名: Kebab-case
タブ数: 4space
最大改行数: 1行

```template
<!DOCTYPE html>
<html lang="ja">

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>APP-NAME</title>
    <link rel="stylesheet" href="path/to/filename.css" rel="stylesheet">
</head>
<body>

<`Example Tag`>
</`Example Tag`>

<script src=”path/to/filename.js”></script>
</body>
</html>
```

注1: スマホ対応の場合のみ下記を記述
```
<meta http-equiv="X-UA-Compatible" content=”IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">
```
注2: scriptタグは`</body>`直前に記述
注3: 相対パスにはカレントディレクトリを記述しない
```bad
<link rel="stylesheet" href="./path/to/filename.css" rel="stylesheet">
```
```good
<link rel="stylesheet" href="path/to/filename.css" rel="stylesheet">
```
注4: body下では基本的に改行はしない。
注5: 属性が多い場合はタグ宣言内で改行
```
<div 
　　　　id="docs-aria-speakable"
  class="a-pk"
  aria-live="assertive"
  role="region"
  aria-atomic="true"
  aria-label="スクリーン リーダーのアナウンス用テキスト"
  aria-relevant="additions"
>
</div>
```
