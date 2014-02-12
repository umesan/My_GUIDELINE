
# CSS & Sass ガイドライン

バージョン：0.1  
最終更新日：2014/02/01


## CSS ＆ Sass 共通ガイドライン

### 概要
CSS・Sassの品質を保つため、CSS, Sass 定義時のルールを設ける。  
この章ではCSSとSassで共通となるルールを定義する。  

CSS・Sassそれぞれのルールに関しては、  
別章「CSSガイドライン」「Sassガイドライン」にて解説。


### 優先順位の設定

CSS・Sassは下記の項目から優先順位をつけて設計。  
新規スタイルの際に迷ったり、既存コードについて疑問に思った際は、設定した優先順位を確認。

> 0. 更新時に、スタイルのコンフリクトによる事故を起こさないこと
> 0. ファイルサイズが軽量であること
> 0. 制作時にclass名で悩まないこと
> 0. スタイルの拡張・修正がしやすいこと
> 0. 複数人で同時作業が可能なこと
> 0. 誰でも更新できること（制作者のSass・CSSの理解度に依存しない）


### Sass導入とCSSの直接編集禁止

特にやむを得ぬ事情がない限りは、Sassを導入。  
Sass環境を構築していない場合は、スタイル編集・制作を原則禁止。  
絶対にCSSファイルは直接編集しない。


### 文字コード
CSS・Sassともに、UTF-8 を採用。
各ファイルの先頭で文字コード宣言を行う。

```css
@charset "UTF-8";
```


### 改行コード
CSS・Sassともに、CR+LF を採用。


### インデント

#### CSSファイル内  
開発時は、半角スペース二つ  
本番配信用ファイルでは、圧縮するためインデントなし


#### Sass（.scss）ファイル内  
タブ（半角4つ分）

> Sassのコンパイル設定によって、出力されるCSSファイル内のインデントは変わる。  
> 　  
> Sassのデフォルト設定では、  
> コンパイル設定をexpandedやnested形式にした場合、  
> 半角2つでインデントがとられる。  
> 　  
> Sassファイル内で、インデントをタブ（半角4つ分）でとった場合でも、  
> 出力されるCSSは、上記デフォルト設定に任せる。  
> 　  
> 同一プロジェクト内において、  
> インデント形式の異なるドキュメントファイルが存在するという事実は、  
> 誠に遺憾ではあるが、以下の理由により許容する。  
> 　  
> 1. 最終的に compressed するためインデントはなくなる  
> 2. Sassを導入した場合、CSSファイルを直接編集しないと決めている  
> 　  
> 　  
> 尚、どうしても我慢ならぬ場合は、  
> 下記を参考にコンパイルされるCSSファイルのインデント形式を変更すること。  
> http://www.skyward-design.net/blog/archives/000121.html



### フォント

#### px
フォントサイズは、pxで指定。  
デフォルトフォントは14pxを基準 (bodyにfont-size: 14pxを指定) とする。  
  
文字サイズはpx固定だが、文字数が増えたり、文字サイズが大きくなったりしても、  
文字がコンテンツ領域に収まるように考慮して、マークアップを行う。  

#### font-family

font-family は、下記を指定。
```css
fontFamily : "メイリオ",Meiryo,"ＭＳ Ｐゴシック","ヒラギノ角ゴ Pro W3","Hiragino Kaku Gothic Pro",sans-serif;
```



### IDセレクタへのスタイル指定禁止
IDセレクタへのスタイルはつけない。  
スタイルはclass に対して指定する。  

#### 理由  
> * IDセレクタに付加したスタイルは再利用ができないため  
> * マルチクラスによる、オーバーライドがしにくくなるため  
> * オーバーライドするために、セレクタを増やすことになるため、結果ファイルサイズが増加する  


### js- プレフィックスを付けたクラスへのスタイル指定禁止
JS用のプレフィックスクラスである js- に対してはスタイルは付加しない。



### h1,h2,h3,h4,h5,h6・・・タグへのスタイル指定禁止
h1,h2,h3,h4,h5,h6 等の見出しタグへの、共通CSSでスタイル付けをおこなわない。  
スタイルを付加する場合は、別途スタイル用のクラス（例、class="m-tit"）を割り当てる。

#### 理由
> h1 や h2 にスタイルを直接付加してしまうと、スタイルに左右されてしまい、決まったエリアにしかh1,h2が使えなくなるため。  
> サイトの構成を見て、用途に応じた適切なマークアップを行うために、h1 や h2 にスタイルを直接付加しない。


### プロパティの値が0の場合は単位を省略する

プロパティの値として 0 を指定する場合は、単位表示を省略する。

```css
/* 採用 */
margin: 0;
padding: 0 10px 0 20px;

/* 非採用 */
margin: 0px;
padding: 0px 10px 0px 20px;
```

#### 理由
> 表記統一のため、pxを必ず記載することも考えたが、さすがに冗長。


### ゼロ以下の値を記述する場合は、0を含める
ゼロ以下の値（0.x）を指定する場合、0は明記する。  

```css
/* 採用 */
font-size: 0.9em;

/* 非採用 */
font-size: .9em;
```

#### 理由
> 見通しを考慮。一瞬でも間違っているかと思うため。


### 色定義

色定義は、16進数で定義し、6桁で記述。  
大文字表記は許容する。  

```css
/* 採用 */
color: #ff0000;
color: #FFFFFF;

/* 非採用 */
color: #f00;
color: red;
```

#### 理由
> 桁数の表記統一のため。
> 
> 大文字の許容の理由は、ChromeのWebインスペクタで色指定をした際、色定義が大文字で返却されるため。
> 制作時にかなりの頻度で利用しコピペを繰り返すため、この点については許容する。


### CSS内の url() 指定に関して
url() ではシングルクォーテーションを使用。  
クォーテーションなしや、ダブルクォーテーションは利用しない。  
CompassのHelper関数利用時も同様。  

```css
/* 採用 */
background-image: url('../img/test.png');
// CompassのHelper関数利用時
background-image: image-url('../img/test.png');

/* 非採用 */
background-image: url(../img/test.png);
background-image: url("../img/test.png");
```

#### 理由
> 表記統一のため。  
> Compassのデフォルト出力時に、シングルクォーテーションが使われているため。


### コメントルール

開発中のコードの見通しをよくするために、各セクションに対して適宜コメントを記述。  
最終的にcssを minify化する際にコメントを削除。

#### 目次
```css
/**
 * PROJECT NAME
 * @require 必要な環境、フレームワーク類があれば記述
 * @version x.x.x
 * @update xxxx/xx/xx
 */
```

#### 大見出し
```css
/*----------------------------------------

 大見出し

----------------------------------------*/
```


#### 中見出し
```css
/*----------------------------------------
 中見出し
----------------------------------------*/
```


#### 小見出し
```css
/* 小見出し */
```



### !important の使用について
ヘルパークラスに使うのは可。  
場当たり的な問題解決として利用するのは禁止。

```css
/* 非採用 */
.error{ color: red !important; }
```


### セレクタとプロパティの記述ルール

スタイルを記述する際は、下記の点に注意。

> * セレクタの直後には半角スペースを記述
> * プロパティの前にはタブ1つでインデント
> * 指定が複数になる場合は基本1行に1プロパティ
> * 指定が少ない場合は1行で記述してもよい
> * セミコロンは省略せず必ず付ける

#### 複数行の場合
```css
.selector {
  property1: value1;
  property2: value2;
}
```

#### 1行の場合
```css
.selector { property3: value3; }
```


Sassを導入している場合、開発環境（expanded）では自動的に上記の形式でCSSが出力される。  
本番環境への反映時(compressed)は、CSSファイルが圧縮されるため、上記のルールには当てはまらなくて問題なし。


### DOMの構成と一致するようにルールセットのインデント

可能であれば、DOMの構成と一致するように  
CSS側もルールセットをインデントを行う。  

#### HTML
```html
<div class="m-header">
  <p class="header-link"></p>
</div>
```

#### CSS
```css
.m-header {
    property: value;
}
    .header-link {
        property: value;
    }
```

#### 理由
> 親子関係が把握できてコードの見通しが良くなるため。  
> 開発時には、こちらのルールを推奨。
> ただし、こちらのルールは強制はしない。






## CSSガイドライン

### 概要

CSSの品質を保つため、CSS定義時のルールを設ける。  
基本的にこちらのルールを遵守。

このCSSガイドラインは、「SassからコンパイルされたCSSファイルが、どういう状態にあるべきか」 を定義する。  


### CSSファイルの外部ファイル化
CSSファイルは外部ファイル化。  

```css
<link rel="stylesheet" href="xxx.css" media="screen">
```


### HTML内、インラインスタイルの禁止
htmlファイルのhead要素内での指定は不可。  

```css
<html lang="ja">
<head>
<meta charset="utf-8">
<title>head内でのスタイル指定は禁止</title>
<style>
.ban{ display: none; }
</style>
</head>
```

htmlファイルに、インラインでのstyle属性での指定も不可


```css
<p style="display: block;">インラインでのスタイル指定禁止</p>
```


### 全体構成

1ファイルにまとめて記述する方式を採用。  
ページ毎のスタイルファイルは持たない。  
スタイルシートの大まかな構成は下記の通り。

> 1. リセットCSS
> 2. サイト独自の初期設定
> 3. サイト独自の汎用（ヘルパー）クラス
> 4. 大枠レイアウト情報
> 5. 個別モジュール


### リセットCSS

リセットCSSは、html5doctor.com Reset Stylesheet v1.6.1 を採用。  
リセットCSSではリセットしきれないスタイルや、サイト制作時に役立つ汎用クラス等は  
リセットCSSのあとに追記しスタイルを上書きする。

```css
/*
html5doctor.com Reset Stylesheet v1.6.1
Last Updated: 2010-09-17
Author: Richard Clark - <a href="http://richclarkdesign.com">http://richclarkdesign.com</a>
*/
html, body, div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
abbr, address, cite, code,
del, dfn, em, img, ins, kbd, q, samp,
small, strong, sub, sup, var,
b, i,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, figcaption, figure,
footer, header, hgroup, menu, nav, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
}
 
body {
  line-height: 1;
}
 
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
  display: block;
}
 
nav ul {
  list-style: none;
}
 
blockquote, q {
  quotes: none;
}
 
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
 
a {
  margin: 0;
  padding: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
}
 
/* change colours to suit your needs */
ins {
  background-color: #ff9;
  color: #000;
  text-decoration: none;
}
 
/* change colours to suit your needs */
mark {
  background-color: #ff9;
  color: #000;
  font-style: italic;
  font-weight: bold;
}
 
del {
  text-decoration: line-through;
}
 
abbr[title], dfn[title] {
  border-bottom: 1px dotted;
  cursor: help;
}
 
table {
  border-collapse: collapse;
  border-spacing: 0;
}
 
/* change border colour to suit your needs */
hr {
  display: block;
  height: 1px;
  border: 0;
  border-top: 1px solid #cccccc;
  margin: 1em 0;
  padding: 0;
}
 
input, select {
  vertical-align: middle;
}
```


### サイト独自の初期設定

リセットCSSの適用後に、サイト独自の初期設定を任意で加える。

* 基準フォントの指定
* スクロールバー色の指定
* リンクの指定
* Tableの初期化
* clearfixの追加
* スマホサイト用の初期化指定等


### サイト独自の汎用(ヘルパー)クラス

独自の初期設定後、サイト制作時によく利用するシングルプロパティクラスを記述する。  
例外のモジュールやエリアへのスタイル指定として利用する。

下記は、参考例。

```
/*----------------------------------------
 Single-propaty for space
----------------------------------------*/
.pt0, .ptb0, .pa0 {
  padding-top: 0px !important;
}
 
.pr0, .prl0, .pa0 {
  padding-right: 0px !important;
}
 
.pb0, .ptb0, .pa0 {
  padding-bottom: 0px !important;
}
 
.pl0, .prl0, .pa0 {
  padding-left: 0px !important;
}
 
.mt0, .mtb0, .ma0 {
  margin-top: 0px !important;
}
 
.mr0, .mrl0, .ma0 {
  margin-right: 0px !important;
}
 
.mb0, .mtb0, .ma0 {
  margin-bottom: 0px !important;
}
 
.ml0, .mrl0, .ma0 {
  margin-left: 0px !important;
}
  
 
/*----------------------------------------
 Single-propaty for font
----------------------------------------*/
.fwb {
  font-weight: bold !important;
}
 
.fwn {
  font-weight: normal !important;
}
 
/*----------------------------------------
 Single-propaty for text-decoration
----------------------------------------*/
.tdu {
  text-decoration: underline !important;
}
 
.tdn {
  text-decoration: none !important;
}
 
/*----------------------------------------
 Single-propaty for visibility
----------------------------------------*/
.vh {
  visibility: hidden !important;
}
 
.vv {
  visibility: visible !important;
}
 
/*----------------------------------------
 Single-propaty for float
----------------------------------------*/
.fl {
  float: left !important;
}
 
.fr {
  float: right !important;
}
 
.fn {
  float: none !important;
}
 
/*----------------------------------------
 Single-propaty for text-align
----------------------------------------*/
.tal {
  text-align: left !important;
}
 
.tar {
  text-align: right !important;
}
 
.tac {
  text-align: center !important;
}
 
/*----------------------------------------
 Single-propaty for vertical-align
----------------------------------------*/
.vat {
  vertical-align: top !important;
}
 
.vam {
  vertical-align: middle !important;
}
 
.vab {
  vertical-align: bottom !important;
}
 
/*----------------------------------------
 Single-propaty for position
----------------------------------------*/
.pr {
  position: relative !important;
}
 
.pa {
  position: absolute !important;
}
 
/*----------------------------------------
 Single-propaty for display
----------------------------------------*/
.db {
  display: block !important;
}
 
.di {
  display: inline !important;
}
 
.dn {
  display: none !important;
}
 
.dib {
  display: inline-block !important;
}
 
.dt {
  display: table !important;
}
 
.dtc {
  display: table-cell !important;
}
 
/*----------------------------------------
 Single-propaty for margin
----------------------------------------*/
.mrla {
  margin-left: auto !important;
  margin-right: auto !important;
}
 
/*----------------------------------------
 Single-propaty for Width
----------------------------------------*/
.w-full {
  width: 100%;
}
 
.w-half {
  width: 50%;
}
 
.w-third {
  width: 33.3%;
}
 
.w-quater {
  width: 25%;
}
 
.w-fifth {
  width: 20%;
}
 
/*----------------------------------------
 Single-propaty for image Replace
----------------------------------------*/
.ir {
  text-indent: 100%;
  white-space: nowrap;
  overflow: hidden;
}
 
/*----------------------------------------
 Single-propaty for ellipsis
----------------------------------------*/
.elp {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```






## Sass ガイドライン


### @import をする際のルール

パーシャルファイルの読み込み指定は、拡張子や接頭辞の_（アンダースコア）を略した表記も可能ではあるが、  
時間を置いてファイルを見直した際や、第三者への引継ぎの際に、直感的にimport先を理解することができないため、  
必ずアンダースコアや拡張子を省略しないで記述する。

```css
@import "_xxx.scss";
@import "_yyy.scss";
```

下記の形でも読み込める。
```css
@import "_xxx";
@import "yyy";
```

また、@importが複数ある場合、1行で書くこともできるが、
可読性が落ちるため採用しない。
```css
@import "_xxx.scss", "_yyy.scss";
```

### ネストの深さ
基本3レベルまで。

#### 理由
> ネストが深くなると、汎用性がなくなるため  
> また、ファイルサイズが増加するため  

＜参考サイト＞
> [Nestが深い - ぼくのかんがえたさいきょうのしーえしゅえしゅ](http://t32k.me/mol/log/the-perfect-css-i-thought/)


### Mixin ファイルの構造

#### 基本構造
セレクタごと出力するようなmixinでは、意図せず重複したセレクタが出力されないように、  
下記の構造で mixin 化する。

```css
$m-XXXX: false !default;
@mixin m-XXXX() {
  @if $m-XXXX {}
  @else {
    $m-XXXX: true;
    .m-XXXX {
    }
  }
}
```

#### 理由
>セレクタごと（.m-XXXX{}のように）出力するような、mixin を作る場合、  
>sassファイルの各場所で、そのmixin が @includeで呼び出された際に、  
>@include　された数だけ、そのクラスが出力されてしまうことになる。  
>  
>コンパイル後のCSSファイル内に、重複したセレクタが増え、  
>ファイル容量やパフォーマンスの面でも好ましくない。  
>  
>そこで、意図せず、@include を複数された場合でも、  
>セレクタが重複して出力されないように、  
>すでに一度　mixinが　@include　されている場合は、  
>2度目以降は　@include　されても中身を出力しないようにするmixin構造を採用する。

＜参考サイト＞
> [参考URL - Sass で Singleton を実現し、安心してクラスを再利用する](http://nodot.jp/articles/singletoninsass.html)  
> [参考URL - Sass 3.2 からは placeholder selector を使おう](http://nodot.jp/articles/placeholderselector.html)


### モジュール記述ルール

モジュールを作成する際は、下記の命名規則で作成する。

* モジュールはm-はじまり
* 単語の区切りはハイフン
* モジュールの子要素は、モジュール名からm-をのぞいたものを引継ぐ

```css
.m-hoge{
    .hoge__item{
    }
    .hoge__txt{
    }
}
```


### モジュールの子要素のクラス名

モジュールの子要素に付けるクラス名はわかりやすいものにする。  
もし、クラス名指定に迷ったら下記のクラス名を積極的に利用する。  

```css
hoge__body
hoge__area
hoge__item
hoge__thumb
hoge__img
hoge__title
hoge__txt
hoge__num
hoge__lnk
```




### 参考文献

> ＜CSS-Guidelines＞  
> https://github.com/kiwanami/CSS-Guidelines/blob/master/README.ja.md
> 
> ＜ぼくのかんがえたさいきょうのしーえしゅえしゅ － MOL＞  
> https://github.com/kiwanami/CSS-Guidelines/blob/master/README.ja.md
> 
> ＜メンテナブルCSS | 株式会社サイバーエージェント＞  
> http://www.cyberagent.co.jp/recruit/techreport/report/id=7926
> 
> ＜「Google HTML/CSS Style Guide」を適当に和訳してみた＞  
> http://re-dzine.net/2012/05/google-htmlcss-style-guide/
> 

### 参考ツール
CSS記述の際に参考になるサイト。

> ＜W3c - CSS Validation Service＞  
> http://jigsaw.w3.org/css-validator/
> 
> ＜Can I use...＞  
> http://caniuse.com/
> 
