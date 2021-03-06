# GET /1/orders

注文情報の一覧を取得

## scope

read_orders

## リクエストパラメーター

| Name          | Description                                                 |
|---------------|-------------------------------------------------------------|
| start_ordered | 注文日時はじめ yyyy-mm-dd または yyyy-mm-dd hh:mm:ss (任意) |
| end_ordered   | 注文日時おわり yyyy-mm-dd または yyyy-mm-dd hh:mm:ss (任意) |
| limit         | リミット (任意 デフォルト: 20, MAX: 100)                    |
| offset        | オフセット (任意 デフォルト: 0)                             |

## レスポンスの例
```
{
  "orders":[
    {
      "unique_key":"154D88A39E454289",
      "ordered":1396419762,
      "payment":"cod",
      "first_name":"山田",
      "last_name":"太郎",
      "total":2000,
      "terminated":true
    },
    {
      "unique_key":"9CD3594222D78673",
      "ordered":1392345522,
      "payment":"bt",
      "first_name":"山田",
      "last_name":"花子",
      "total":3500,
      "terminated":false
    }
  ]
}
```

## 解説

* unique_key - 注文情報を識別するユニークなキー
* ordered - 注文日時
* payment - 決済方法。creditcard:クレジットカード決済、bt:銀行振込(ショップ口座)、cod:代金引換、cvs:コンビニ決済、base_bt:銀行振込(BASE口座)
* total - 合計金額 (消費税、手数料含む)
* terminated - すべてが発送済みかキャンセルになっていればtrue

## エラーレスポンスの例

```
{
  "error":"access_denied",
  "error_description":"httpsでアクセスしてください。"
}
```
```
{
  "error":"invalid_request",
  "error_description":"アクセストークンが無効です。"
}
```
```
{
  "error":"invalid_scope",
  "error_description":"スコープが無効です。"
}
```
