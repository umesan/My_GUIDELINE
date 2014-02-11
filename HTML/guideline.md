# HTML コーディング ガイドライン

バージョン：0.1  
最終更新日：2014/02/01

## はじめに
XXXXX のコーディング ガイドラインです。  


## HTML

### ドキュメントタイプ
HTML5

<pre>
&lt;!DOCTYPE html&gt;
&lt;html lang="ja"&gt;
</pre>


### エンコード
UTF-8 （BOM無し）
<pre>
<meta charset="utf-8">
</pre>


### インデント
タブ(半角4つぶん)を使用


### 改行コード
CR+LF


### 閉じタグについて
終了タグを省略して表記

<pre>
<!-- 採用 -->
<meta charset="utf-8">
<br>
&lt;img src="xxx.png" alt="xxxx" width="100" height="100"&gt;

<!-- 非採用 -->
<meta charset="utf-8" />
<br />
&lt;img src="xxx.png" alt="xxxx" width="100" height="100" /&gt;
</pre>


### type属性の省略
link や script タグの type属性を省略して表記。

<pre>
<!-- 採用 -->
&lt;script src="xxxx.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="xxx.css"&gt;

<!-- 非採用 -->
&lt;script type="text/javascript" src="xxxx.js"&gt;&lt;/script&gt;
&lt;link type="text/css" rel="stylesheet" href="xxx.css"&gt;
</pre>


### プロトコルの省略
プロトコルを省略して表記

<pre>
<!-- 採用 -->
&lt;script src="//ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"&gt;&lt;/script&gt;
<!-- 非採用 -->
&lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"&gt;&lt;/script&gt;
</pre>


### 小文字
小文字のみ使用する

<pre>
<!-- 採用 -->
<div>TEXT<br>TEXT</div>
<!-- 非採用 -->
<DIV>TEXT<BR>TEXT</DIV>
</pre>


### 代替テキスト
代替テキストが必要な画像には、altを記述
意味をもたない画像の場合、代替テキストは alt=""とする

<pre>
<!-- 採用 -->
<img src="xxx.png" alt="" width="200" height="150">
<!-- 非採用 -->
<img src="xxx.png" width="200" height="150">
</pre>

### 実態参照について
特殊文字は実態参照で表記。

<pre>
&amp;  →  &amp;amp;
&copy;  →  &amp;copy;
&lt;  →  &amp;lt;
&gt;  →  &amp;gt;
&#12316; →  &amp;#12316;
</pre>


### コメント
第三者が内容を把握しやすくするため、適宜コメントを記述。  


### BEM
BEMのルールでコーディング。
<pre>
	block__element--modifier
</pre>

モジュールに対しては、接頭辞「m-」を付加する。
<pre>
<header class="m-header">
	<div class="header__txt">HEADER</div>
</header>
<a class="m-btn01"></a>
</pre>

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
