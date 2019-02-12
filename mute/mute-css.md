# 簡易ミュート用CSSのメモ
初稿：2019/2/12  

## 概要
おしゃべりルームで簡易的に投稿の本文をミュートするためのCSSのメモです。  
CSSを変更できるChrome機能拡張などでご利用ください。  
  
**いかなる損害の責任も負えません。**  
**自己責任でのご利用をお願いします。**  
  
## CSS
`よよよよ`の部分は各自で書き換えてください。(そのままでもいいけど)
  
### ■完全に見えなくする
完全に消します。読めません。
```css
[data-user-display-name="よよよよ"] :nth-child(4) {
    display: none;
}
```
  
### ■本文の文字色を白にする
白文字になるので見えなくなります。  
マウスで本文を範囲選択すると、背景色が反転して読めるようになります。
```css
[data-user-display-name="よよよよ"] :nth-child(4) {
    color: #fff;
}
```
  
### ■本文にマウスポインタを重ねると文字色が白から黒に変化する
白文字＆本文エリアの縮小で見えなくしてありますが、  
マウスポインタを本文に重ねると本文が展開されて文字色が白から黒へと変化します。
```css
[data-user-display-name="よよよよ"] :nth-child(4) {
    color: #fff;
    height: 15px;
    overflow: hidden;
}

[data-user-display-name="よよよよ"] :nth-child(4):hover {
    color: #333;
    height: auto;
    transition: 5s;
}
```
文字色の変化スピードは`transition: 5s;`で5秒に設定してあります。  
ご自身の感覚に合わせて変更してください。
