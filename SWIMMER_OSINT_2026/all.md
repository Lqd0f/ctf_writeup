## debeyohiru_01_social
>調査対象の人物はソフトウェアエンジニアで、2026年以降には debeyohiru というIDでの活動が確認されています。この人物がこのIDでの活動を開始したのは2026年1月のようです。この人物がこれ以前に使用していたIDを特定できないでしょうか？2026年1月時点で、noteというサービスに古いIDのアカウントが残存しているようです。このアカウントのIDを解答してください。

　`debeyohiru`でsherlockをかけてみると[Blueskyのアカウント](https://bsky.app/profile/debeyohiru.bsky.social)がヒットする(一応普通のGoogle検索でも同様のアカウントを見つけることが可能だったようです)．
```
$ sherlock debeyohiru
[*] Checking username debeyohiru on:

[+] Bluesky: https://bsky.app/profile/debeyohiru.bsky.social
[+] note: https://note.com/debeyohiru
[+] BabyRu: https://www.baby.ru/u/debeyohiru

[*] Search completed with 3 results
```

　アカウントを遡ってみると
https://bsky.app/profile/debeyohiru.bsky.social/post/3mavlx6v3ak2c
 
　この投稿には，以下の画像が添付されている．
![](https://cdn.bsky.app/img/feed_thumbnail/plain/did:plc:wgxr2fnwbyylu2bj3cx3lrfm/bafkreihzjfyphc47idqh5icgii7yjwv5wi34fthzntfx7whq77cmz27hiq@jpeg)

　アドレスバーから，`furaigo5`というIDを使用していたことがわかる．
:::details flag
SWIMMER{furaigo5}
:::

## debeyohiru_02_profile
>debeyohiru は2026年1月時点で求職中で、プロフィールページをウェブ上に公開していたようです。
このページを探り出し、そのURLを解答してください。

　今度は`furaigo5`でsherlockをかけてみる．今度は[GitHubのアカウント](https://www.github.com/furaigo5)がヒット．
 ```
$ sherlock furaigo5
[*] Checking username furaigo5 on:

[+] GitHub: https://www.github.com/furaigo5
[+] livelib: https://www.livelib.ru/reader/furaigo5
[+] note: https://note.com/furaigo5
[+] BabyRu: https://www.baby.ru/u/furaigo5

[*] Search completed with 4 results
```
　コミットの痕跡やリポジトリはないが，プロフィールにPagesがリンクされいる．
https://furaigo5.github.io/profile/
:::details flag
SWIMMER{https\://furaigo5.github.io/profile}
:::

## debeyohiru_03_email
>debeyohiru が2026年現在、普段使っているメールアドレスが知りたいです。この人物が現在使用中とおぼしきメールアドレスを探り出し、解答してください。

 02で見つけたプロフィールページの`Contact`に記載されている．
 
:::details flag
SWIMMER{furaigo5.onionsoup@gmail.com}
:::

## debeyohiru_04_meal
>debeyohiru はある料理が好物で、よく食べているようです。 直近では2026年1月10日の夕食にその料理を食べたことが確認されています。 この人物がこの日の夕食に食べたメニューを特定し、店舗のメニューに記載された名前で解答してください。

　[Blueskyでの投稿](https://bsky.app/profile/debeyohiru.bsky.social/post/3mazue5yqdc2n)から，12月28日に以下の画像の料理を提供している店で夕食をとっており，1月10日にも同様の店を訪れていることがわかる．
![](https://cdn.bsky.app/img/feed_thumbnail/plain/did:plc:wgxr2fnwbyylu2bj3cx3lrfm/bafkreihk37wk5aaiblyyv3z6nsxiqgy3ykadzvvzepw67pulopprqi3tzy@jpeg)
　皿に"POMME"の印字があるので検索する(もちろん画像検索も使えます)．最上位には出ないが，"ポムの樹"というオムライス専門店がヒット．さらに，プロフィールページからdebeyohiruは渋谷で活動していることがわかっており，渋谷には1店舗しかないので店舗は"ポムの樹 渋谷スペイン坂店"で確定．
　ここで，Google Mapsのクチコミを見てみる(ここに気付くのが難しかったです)．すると，`ふらいご`というユーザのレビューを発見．
```
2026/1/10

冬限定メニューを食べました。
家だとこんなにうまくオムライス作れないので、いつもお世話になっています。今日もおいしかったです。
```
実際のレビュー(一部抜粋)

　このレビューには以下の画像が添付されている．
![](https://lh3.googleusercontent.com/gps-cs/AHvCnQxhw2IlLbIJi9LI4ki8m3pGIcoV4Zm5AmHReQpkaNRezKnn1Sn5cFtVTXw5U5RWZ0EjpArJ8aY6Nofb0i5Cpgaqnws1TTufcZuWhmLAkZ4vXrtTnEqjiEj67YQNpufkFPF95D_0mQusdqjh=w750-h401-p-k-no)

　レビューから，冬限定メニューであることがわかるので"ポムの樹 渋谷スペイン坂店 冬限定メニュー"で検索．公式Xの投稿がヒット．
https://x.com/pomunoki_offl/status/1998577131329302632

　添付画像一番上のメニューがレビューの料理と一致する．
 
:::details flag
SWIMMER{豚肉とリンゴのホタテトマトクリームオムライス}
:::

## debeyohiru_05_hidden1
>debeyohiru の本名が知りたいです。この人物の実名と考えられるものを解答してください。

　プロフィールページをデベロッパツールで解析してみる．"ソース"から`script.js`を覗いてみると，documentのauthorに本人と思われる名前が書かれている．
 
:::details flag
SWIMMER{Gotanno Tsubasa}
:::

## debeyohiru_06_hidden2
>debeyohiru が 2025年12月 時点で使用していたと考えられるスマートフォンの機種が知りたいです。なお、複数の端末を使用していたと考えられる場合は、アンダーバー（_）で繋いで全てを解答してください。

　[Blueskyでの投稿](https://bsky.app/profile/debeyohiru.bsky.social/post/3mc2lwrkq2s2c)から，現在のプロフィールページの情報は12月時点のものとは違うことが推測できる．そのため，情報が更新される前の魚拓を探す．
　Wayback Machineには残っていなかったが，[Archive.today](https://archive.md)では2026/1/2時点(投稿日より，1月10日よりも前の情報であれば十分です)のものを発見することができた．
https://archive.md/ORR6S

:::details flag
SWIMMER{Pixel 8 Pro_iPhone 13 mini}
:::
