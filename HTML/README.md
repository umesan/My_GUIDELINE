
# HTML コーディング ガイドライン

バージョン：0.1  
最終更新日：2014/02/01

## はじめに

HTMLの品質を一定に保つため、HTML記述時のルールを設ける  
特に指定がない場合はこちらのルールを遵守すること


## HTML

### ドキュメントタイプ
HTML5

```html
<!DOCTYPE html>
<html lang="ja">
```

### エンコード
UTF-8 （BOM無し）
```html
<meta charset="utf-8">
```


### インデント
タブ(半角4つぶん)を使用


### 改行コード
CR+LF


### 閉じタグについて
終了タグを省略して表記

```html
<!-- 採用 -->
<meta charset="utf-8">
<br>
<img src="xxx.png" alt="xxxx" width="100" height="100">

<!-- 非採用 -->
<meta charset="utf-8" />
<br />
<img src="xxx.png" alt="xxxx" width="100" height="100" />
```


### type属性の省略
link や script タグの type属性を省略して表記
```html
<!-- 採用 -->
<script src="xxxx.js"></script>
<link rel="stylesheet" href="xxx.css">

<!-- 非採用 -->
<script type="text/javascript" src="xxxx.js"></script>
<link type="text/css" rel="stylesheet" href="xxx.css">
```


### プロトコルの省略
プロトコルを省略して表記

```html
<!-- 採用 -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>

<!-- 非採用 -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
```


### タグ及び属性の表記
小文字のみ使用

```html
<!-- 採用 -->
<div>TEXT<br>TEXT</div>

<!-- 非採用 -->
<DIV>TEXT<BR>TEXT</DIV>
```


### 代替テキスト
代替テキストが必要な画像には、altを記述  
意味をもたない画像の場合、代替テキストは alt=""とする

```html
<!-- 採用 -->
<img src="xxx.png" alt="" width="200" height="150">

<!-- 非採用 -->
<img src="xxx.png" width="200" height="150">
```

### 実態参照について
特殊文字は実態参照で表記

```html
&  →  &amp;
©  →  &copy;
<  →  &lt;
>  →  &gt;
〜 →  &#12316;
```


### コメント
第三者が内容を把握しやすくするため、適宜コメントを記述  

```html
<!-- コメント -->
```

### BEM
BEMのルールでコーディング

```html
	block__element--modifier
```

モジュールに対しては、接頭辞「m-」を付加する。
```html
<header class="m-header">
	<div class="header__txt">HEADER</div>
</header>
<a class="m-btn01"></a>
```

> ＜BEMについて＞  
> https://github.com/juno/bem-methodology-ja/blob/master/definitions.md
>
> ＜実践 めんどうくさくない BEM＞  
> http://tsmd.hateblo.jp/entry/2013/12/12/004059
>
> ＜MindBEMding＞  
> http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
>
> ＜BEM とは＞  
> http://chroma.hatenablog.com/entry/2013/12/12/200817
