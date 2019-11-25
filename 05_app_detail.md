# アプリケーション設計

## 全体
- トップページ(アクション：root, URL："/")の記載がない
- ユーザーと管理者のURLは分ける。namespace使う
- deviseで生成されるpathも記述する
- 購入履歴を表すpathがない
- 注文確認画面のpathがない
- 支払い方法の選択画面のpathがない
- 支払い方法変更した場合の更新pathがない
- 退会確認画面のpathがない
- 退会完了画面のpathがない
- 論理削除を使用するモデルについては、DELETEメソッドは不要です。

## admins
- editコントローラのpathは/admins/:id/edit

## orders
- newコントローラのpathは/orders/new

## order_details
- orderのcreateアクション内で、同時にorder_detailsテーブルの内容も登録するため不要
