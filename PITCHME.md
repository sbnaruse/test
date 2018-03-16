# Discovery 自然言語クエリーの学習

---

## 学習データ

自然言語の質問文と、対応する実例のリスト

### 実例のリスト

ドキュメントIDと関連性ラベルのペア

### 関連性ラベル

0〜100の範囲の整数で、質問文とドキュメントとの関連性を表す。

ツールキットでは関連性なしを0、関連性ありを10に設定している。

---

## 学習データのフォーマット

``` json
{
  "query_id": "string",
  "natural_language_query": "string",
  "filter": "string",
  "examples": [
    {
      "document_id": "string",
      "cross_reference": "string",
      "relevance": 0
    }
  ]
}
```

---


## 学習の要件

- 最低４９セットの学習データが必要

- 実例に使用するドキュメントは検索結果の100以内である必要がある

- 実例の関連性ラベルは関連あり・なしの両方が含まれる必要がある

- フィルターを使用する場合は、本番と同じものを使用する必要がある

上記の要件を満たし次第、自動でトレーニングが開始される

---

## 学習状況照会結果の例

``` json
 {
   "collection_id": "99040100-fe6a-4782-a4f5-28f9eee30850",
   ...
   },
   "training": {
     "total_examples": 54,
     "available": true,
     "processing": false,
     "minimum_queries_added": true,
     "minimum_examples_added": true,
     "sufficient_label_diversity": false,
     "notices": 13,
     "successfully_trained": "2017-02-08T14:18:22.786Z",
     "data_updated": "2017-02-10T14:18:22.786Z"
   }
 }
```

---

### training フィールドの説明

|名前|説明|
|:----|:----|
|processing|trueの場合、トレーニング中|
|available|trueの場合トレーニングが完了し、モデルを使用可能|
|successfully_trained|トレーニングが完了した時刻|
|data_updated|successfully_trainedより新しい日時の場合、トレーニング後に新たなデータが追加されている|
 

### トレーニングの要件が満たされているかどうかは、下記のフィールドで確認できる。全てtrueになっていれば満足している。

- minimum_queries_added
	 
- minimum_examples_added

- sufficient_label_diversity


