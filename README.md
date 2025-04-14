# accountSelect
iOSでChromeを使用する際、アカウントの切り替えがめんどくさいと思ったので、その対策として作りました。

---

**使用するアプリ・扱うファイル**


・ショートカット

・中継サイトを作成するhtml（今回だと"relay.html"）

・中継サイトのレイアウトなどの視覚情報を整理するcss（"style.css"）

---

**処理の流れ**


1．discordで対象となるリンクを長押し

2．「リンクを共有」をタップ

3．対応するショートカット名を、共有シートから選択

4．ショートカット内で、リンクのエンコード処理＆中継先リンクとエンコード済みリンクを結合

5．結合済みのテキストからURLを取得し、Chromeで開く

6．中継サイトで使用したいアカウントを選択

7．元リンクへと遷移



---

**注意点**


・初めてのツール作成ということで拙い部分がいくつか見受けられるため、ちょっとした参考程度に見ていただけると幸いです。

・まだ開発段階のため、一部リンクで動作しない可能性があります。加えて、正常に動作しているかも怪しいです。

・(今回は限定的に、discordの外部リンクでChromeへと遷移する場合のみを想定)



---

**relay.html**


・URL内の"authuser"パラメータを使用して、現在のアカウントを区別しているようなので、それを利用してアカウントを選択おできるようにした

（なお、このパラメータはアカウントログインした順に0, 1, 2...と割り振られる模様）


・「https://blender-kuma-benefit.github.io/accountSelect/relay.html」が中継サイトのリンクとなり、その後ろに「?target=【エンコード済みリンク】」をくっつけることで、元のリンク先へ飛べるようにしている

---

**ショートカット**

・エンコードに関して、ショートカットのアクション「URLエンコード」を選択した場合、":"や"/"などの本来エンコードしてはいけない予約文字などをエンコードしない

    ●今回は中継リンク内に元のリンクを埋め込むので、元リンクは完全にエンコードしなければならない
    
・そのため、「テキストを置き換え」アクションをたくさん使うという力業で、エンコードを行っている

・本リポジトリの「Googleアカウント切り替えツール.shortcut」が該当ファイル

