# 名刺入力サイト用ユーザーCSS
初稿：2019.3.3　更新：2019.3.7
  
某名刺入力業務の外部サイトのCSSをいじって遊ぶメモです。

## おやくそく

**いかなる損害の責任も負えません。**  
**自己責任でのご利用をお願いします。**  
  
名刺の入力作業前には、毎回必ずユーザーCSSをオフにして、サイトの仕様に変更が無いかを確認しましょう。  
（CSSをいじっていたから仕様変更に気が付かなかったなんて事故が起こらないように！！）  
  
私はChrome機能拡張の Stylus を利用しています。  
Stylus を使う場合、適用先は「次で始まるURL」に設定し、  
名刺入力画面のURLの前半部分( `https://あのサイト/あの記号/あの単語/` ) を指定すればよいでしょう。  

## CSS
コピペでどうぞ。  
色など、各自でいじってみてください。  

### ■名刺の回転ボタンの位置を変更する
ベストポジションは未だわからずなのですが、とりあえず名刺の右上に変更してみました。  

```css
/* ボタンの配置 */
.btn-rotate {
    position: relative;
    float:right;
}

/* ボタンの色 */
.btn-rotate md-icon {
    color: crimson;
}

/* ボタンの背景 */
.shadow {
    display: none;
}
```

### ■完了ボタンを信号っぽくする
最後の確認画面でエンターキーを連打しているみなさん用。  
完了ボタンが赤→緑に変化してからエンターキーを押しましょう。

```css
.md-button.md-accent.md-raised:not([disabled]) {
    background-color: #f00;
}
```

### ■白背景をグレーモードにする
最初はダークモードを作ろうと思ったのだけど、  
名刺画像の白が逆に目に刺さるような感じがしたのでグレーにしてみました。  
お気に召さない場合は `background-color` や `color` の色を変更してみてください。  

```css
/* ルール：文字色 */
.precautions {
    color: crimson;
}

/* 入力欄：背景色・文字色 */
#full_name,
#phone,
#email,
#email_id,
#email_domain,
#company,
#department,
#position,
#address,
#tel,
#fax {
    background-color: hsl(0, 0%, 93%);
    color: hsl(0, 0%, 20%);
}

/* プレースホルダー：文字色 */
#full_name::placeholder,
#phone::placeholder,
#email::placeholder,
#email_id::placeholder,
#email_domain::placeholder,
#company::placeholder,
#department::placeholder,
#department::placeholder,
#position::placeholder,
#address::placeholder,
#tel::placeholder,
#fax::placeholder {
    color: hsl(0, 0%, 85%);
}

/* 背景色 */
/* └[ツールバー] */
md-toolbar.md-hue-3.md-menu-toolbar,
/* └[メインエリア] */
md-content,
/* └[確認画面] */
md-sidenav,
md-sidenav md-content {
    background-color: hsl(0, 0%, 90%);
}

/* 項目ラベル：文字色 */
md-input-container label {
    color: crimson !important;
}
```

### ■項目ラベルにアイコンをつける

項目ラベルの前にシンプルなアイコンを表示します。  
  
アイコンの色は `content: url()` 内でHEX値 `dc143c` にしてあります。  
変更したい場合はエディタなどで `dc143c` を検索し、お好みの色のHEX値に置換して下さい。  
  
SVGアイコン素材提供元  
　ICONSVG ( https://iconsvg.xyz )  
　Created by @gaddafirusli ( http://twitter.com/gaddafirusli )  
　MIT License ( https://opensource.org/licenses/MIT )  

```css
/* 姓名 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(3) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M20%2021v-2a4%204%200%200%200-4-4H8a4%204%200%200%200-4%204v2%22%3E%3C%2Fpath%3E%3Ccircle%20cx%3D%2212%22%20cy%3D%227%22%20r%3D%224%22%3E%3C%2Fcircle%3E%3C%2Fsvg%3E");
}

/* 携帯*/
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(4) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Crect%20x%3D%225%22%20y%3D%222%22%20width%3D%2214%22%20height%3D%2220%22%20rx%3D%222%22%20ry%3D%222%22%3E%3C%2Frect%3E%3Cline%20x1%3D%2212%22%20y1%3D%2218%22%20x2%3D%2212%22%20y2%3D%2218%22%3E%3C%2Fline%3E%3C%2Fsvg%3E");
}

/* メール */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(5) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M4%204h16c1.1%200%202%20.9%202%202v12c0%201.1-.9%202-2%202H4c-1.1%200-2-.9-2-2V6c0-1.1.9-2%202-2z%22%3E%3C%2Fpath%3E%3Cpolyline%20points%3D%2222%2C6%2012%2C13%202%2C6%22%3E%3C%2Fpolyline%3E%3C%2Fsvg%3E");
}

/* メールのID*/
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(5) email-id-field label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M20.84%204.61a5.5%205.5%200%200%200-7.78%200L12%205.67l-1.06-1.06a5.5%205.5%200%200%200-7.78%207.78l1.06%201.06L12%2021.23l7.78-7.78%201.06-1.06a5.5%205.5%200%200%200%200-7.78z%22%3E%3C%2Fpath%3E%3C%2Fsvg%3E");
}

/* 会社 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(6) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M4%2015s1-1%204-1%205%202%208%202%204-1%204-1V3s-1%201-4%201-5-2-8-2-4%201-4%201z%22%3E%3C%2Fpath%3E%3Cline%20x1%3D%224%22%20y1%3D%2222%22%20x2%3D%224%22%20y2%3D%2215%22%3E%3C%2Fline%3E%3C%2Fsvg%3E");
}

/* 部署 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(7) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M8%203H5a2%202%200%200%200-2%202v3m18%200V5a2%202%200%200%200-2-2h-3m0%2018h3a2%202%200%200%200%202-2v-3M3%2016v3a2%202%200%200%200%202%202h3%22%3E%3C%2Fpath%3E%3C%2Fsvg%3E");
}

/* 役職 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(8) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Ccircle%20cx%3D%2212%22%20cy%3D%2212%22%20r%3D%2210%22%3E%3C%2Fcircle%3E%3Cline%20x1%3D%2212%22%20y1%3D%2216%22%20x2%3D%2212%22%20y2%3D%2212%22%3E%3C%2Fline%3E%3Cline%20x1%3D%2212%22%20y1%3D%228%22%20x2%3D%2212%22%20y2%3D%228%22%3E%3C%2Fline%3E%3C%2Fsvg%3E");
}

/* 住所 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(9) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Ccircle%20cx%3D%2212%22%20cy%3D%2210%22%20r%3D%223%22%2F%3E%3Cpath%20d%3D%22M12%2021.7C17.3%2017%2020%2013%2020%2010a8%208%200%201%200-16%200c0%203%202.7%206.9%208%2011.7z%22%2F%3E%3C%2Fsvg%3E");
}

/* TEL */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(10) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpath%20d%3D%22M22%2016.92v3a2%202%200%200%201-2.18%202%2019.79%2019.79%200%200%201-8.63-3.07%2019.5%2019.5%200%200%201-6-6%2019.79%2019.79%200%200%201-3.07-8.67A2%202%200%200%201%204.11%202h3a2%202%200%200%201%202%201.72%2012.84%2012.84%200%200%200%20.7%202.81%202%202%200%200%201-.45%202.11L8.09%209.91a16%2016%200%200%200%206%206l1.27-1.27a2%202%200%200%201%202.11-.45%2012.84%2012.84%200%200%200%202.81.7A2%202%200%200%201%2022%2016.92z%22%3E%3C%2Fpath%3E%3C%2Fsvg%3E");
}

/* FAX */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(11) label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Cpolyline%20points%3D%226%209%206%202%2018%202%2018%209%22%3E%3C%2Fpolyline%3E%3Cpath%20d%3D%22M6%2018H4a2%202%200%200%201-2-2v-5a2%202%200%200%201%202-2h16a2%202%200%200%201%202%202v5a2%202%200%200%201-2%202h-2%22%3E%3C%2Fpath%3E%3Crect%20x%3D%226%22%20y%3D%2214%22%20width%3D%2212%22%20height%3D%228%22%3E%3C%2Frect%3E%3C%2Fsvg%3E");
}

/* ドメイン */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(6) email-domain-field label::before {
    content: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2024%2024%22%20fill%3D%22none%22%20stroke%3D%22%23dc143c%22%20stroke-width%3D%223%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%3E%3Ccircle%20cx%3D%2212%22%20cy%3D%2212%22%20r%3D%224%22%3E%3C%2Fcircle%3E%3Cpath%20d%3D%22M16%208v5a3%203%200%200%200%206%200v-1a10%2010%200%201%200-3.92%207.94%22%3E%3C%2Fpath%3E%3C%2Fsvg%3E");
}

/* アイコン表示部の余白調整 */
div.typing.ng-scope.layout-column.flex-50 > div > :nth-child(n) label::before {
    display: inline-block;
    width: 35px;
    height: 40px;
    vertical-align: middle;
}

/* アイコンOFF */
div.typing.ng-scope.layout-column.flex-50 > div label.f-label-large-blocked::before{
    display: inline-block;
    content: " " ;
    width: 0px;
}

/*
SVGアイコン素材
ICONSVG ( https://iconsvg.xyz )
Created by @gaddafirusli( http://twitter.com/gaddafirusli )
MIT License ( https://opensource.org/licenses/MIT )
*/
```

### ■特定の入力欄をカラーリング

作業を続けていると惰性でミス入力をしそうになったので、  
特定の入力欄をカラーリングして脳を刺激するようにしてみました。  
（携帯番号とメールアドレスが両方記載されてる画像とかのあれ！！  
　あと、役職欄に住所を入力しちゃったり……とほほ）  
  
私はメールアドレス関連・携帯電話・役職の入力欄を装飾しています。  
  
グレーモードのCSSを適用している場合は、  
セレクタの優先度でうまく反映されない場合があるので注意です。  
グレーモードCSSの該当セレクタをコメントアウトするか、  
グレーモードCSSよりも後ろに特定の入力欄のCSS記述するようにして下さい。  

```css
#email,
#email_id {
    background-color: hsl(300, 100%, 85%);
    color: hsl(300, 100%, 40%);
}

#email_domain {
    background-color: hsl(150, 100%, 85%);
    color: hsl(150, 100%, 40%);
}

#email::placeholder,
#email_id::placeholder,
#email_domain::placeholder {
    color: hsla(0, 0%, 100%, .2);
}

#phone,
#position{
    background-color: hsl(240, 100%, 85%);
    color: hsl(240, 100%, 97%);
}

#phone::placeholder,
#position::placeholder {
    color: hsla(0, 0%, 100%, .2);
}
```
ご自身でいじりたい方は下記のIDを参考にどうぞ。  
プレースホルダー（用例）の指定は各IDの末尾に `::placeholder` を追記して下さい。  

|項目|ID|
|:--|:--|
| 姓名 | #full_name |
| 携帯電話 | #phone |
| メール| #email |
| メールのID| #email_id |
| メールのドメイン| #email_domain |
| 会社| #company |
| 部署| #department |
| 役職| #position |
| 住所| #address |
| 会社電話 | #tel |
| FAX | #fax |
