# テーブル定義書Q3

## 全体
- テーブル名は先頭小文字・複数形、復号単語はスネークケースで書く
- カラム名の先頭にテーブル名をつけない
- ステータスはenumでもつため、integer
- PKは基本全部index
- 配送先テーブルがない
- [add] 全てのテーブルで"created_at"が「ユーザー登録日時」に、"updated_at"が「ユーザー更新日時」となっている
- [add] "id"がないテーブルが存在する

## admin
- idにPKの○がない

## users
- user_l_name, user_f_name, user_telのように省略しない
- 郵便番号, 電話番号はstring
- 名前nullを許可しないほうがいい
- 性 → 姓
- [add] 退会ステータスが"member_status"となっているが、なんのステータスか分かりづらいです。"is_deleted"などが良いでしょう。
- [add] 退会ステータスのデータ型を見直す必要があります。どの型が適切か考え、指摘事項に追記して下さい。

## products
- ディスクid, アーティストid, レーベルid, ジャンルidにFKがない
  - [check]下で指摘している通り、idは不要ですので、ここの指摘でディスクidを含める必要はありません。
- ジャケット画像のカラム名は最後にid入る
- カラムの頭についているcd不要
- disc_id不要
- 発売日カラムがない
- 在庫数カラムはもたない
- [add]stock_statusは必要ありません。必要ない理由を考え、指摘事項に追記して下さい。

## discs
- FKは単数形。product_id
- numも省略しない
- [add]track_noはこのテーブルではない
- [add]本来であればER図での指摘ですが、このテーブル構造では同一商品内で異なるディスクかどうかの判断ができません。

## songs
- PKのidがない
- 曲名はカラム名name
  - [check]これに加えて、データ型も確認しましょう。現状integerとなっていますが、適切でしょうか。
- 曲順のカラムがない

## labels
- PKのidがない
- 「レーベル」というより「レーベル名」
- [add] product_idは不要

## artists
- PKのidがない
- アーティスト名はカラムname
- アーティスト名はstring
- [add] product_idは不要

## genres
- PKのidがない
- ジャンル名はカラムname
- [add] product_idは不要
- [add] ジャンル名カラムのデータ型を確認してみましょう。

## cart_items
- PKのidがない
- buy numは省略しない、スネークケースで書く、buyではなくorderとかにする
  - [check]指摘事項はOKです。カラム物理名は"amount"などにすると適切です。
- 商品idのデータ型が抜けてる
- [add] subtotalは必要ありません。必要ない理由を考え、指摘事項に追記して下さい。

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
- [add]buy_detailカラムは不要です。(buy_detailsテーブルの「注文idのFKカラムがない」の部分で指摘しても良いかも)
- [add]支払い方法の"pay"は、支払いの何を表しているのかイメージしづらい

# テーブル定義書Q4
## 全体
- カラム名の先頭にテーブル名をつけない
- PKは基本全部index

## admin

## users
- user_l_name, user_f_name, user_telのように省略しない
- 郵便番号はtext型が望ましい
- 性 → 姓
- [add] 退会ステータスが"member_status"となっているが、なんのステータスか分かりづらいです。"is_deleted"などが良いでしょう。
- [add] "member_status"のデータ型はinteger/enumとなっていますが、型自体はintegerになります。

## ships
- tel省略しない
- 顧客の情報に合わせて姓名など分けた方が良い

## products
- ディスクid, アーティストid, レーベルid, ジャンルidにFKがない
- ジャケット画像はtext型の方が望ましい
- 在庫数カラムはもたない
- 発売日カラムがない

## discs
- num省略しない

## songs
- 曲名はカラム名name

## labels
- レーベル名はカラムname

## artists
- アーティスト名はカラムname

## genres
- ジャンル名はカラムname

## sell details
- テーブル名はorder_detailsなど
- product_idはFK
- numは省略しない
- 購入詳細IDではなく購入ID
- 商品の詳細の情報(名前やジャケット画像などなど)をもっておく必要がある
- [add]購入時の価格が必要です

## Buy
- [check]テーブル名はsellsになっています。
- テーブル名はorderなど
- payというカラム名はわかりにくい
- totalは何のtotalだかわからない
- telは省略しない
- [add] sell_details_idは、リレーションが逆になるので必要ありません。
