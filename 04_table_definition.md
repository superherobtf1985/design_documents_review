# テーブル定義書Q3

## 全体
- テーブル名は先頭小文字・複数形、復号単語はスネークケースで書く
- カラム名の先頭にテーブル名をつけない
- ステータスはenumでもつため、integer
- PKは基本全部index

## admin
- idにPKの○がない
- 指摘事項
- 指摘事項

## users
- user_l_name, user_f_name, user_telのように省略しない
- 郵便番号, 電話番号はstring
- 名前nullを許可しないほうがいい
- 性 → 姓

## products
- ディスクid, アーティストid, レーベルid, ジャンルidにFKがない
- ジャケット画像のカラム名は最後にid入る
- カラムの頭についているcd不要

## discs
- FKは単数形。product_id
- numも省略しない

## songs
- PKのidがない
- 曲名はカラム名name
- 曲順のカラムがない

## labels
- PKのidがない
- 「レーベル」というより「レーベル名」

## artists
- PKのidがない
- アーティスト名はカラムname
- アーティスト名はstring

## genres
- PKのidがない
- ジャンル名はカラムname

## cart_items
- PKのidがない
- buy numは省略しない、スネークケースで書く、buyではなくorderとかにする
- 商品idのデータ型が抜けてる

## Buy details
- テーブル名はorder_detailsなど
- 注文idや商品idのFKカラムがない
- buy numは省略しない、スネークケースで書く、buyではなくorderとかにする
- 注文した商品の情報を保存するカラムがない

## Buy
- order
- 支払い方法もenumで書く
- 支払い合計にstockという単語はおかしい
- 購入日カラムはいらない
- 配送ステータスがない


* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。
