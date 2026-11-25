# AI Knowledge Studio API仕様

## 要約する

- 送信先: `POST /api/v1/summaries`

### 画面からAPIに送るデータ
- `text` は、前後の空白を除いて 1〜5000文字。
- `mode` は、`short` または `detailed`。

```json
{
  "text": "Reactは、画面を部品に分けて組み立てられるJavaScriptライブラリです。",
  "mode": "short"
}
```

### APIから画面に返すデータ

成功時のHTTPステータスは `200`。以下は公開デモ版の応答例。

```json
{
  "summary": "これはデモ用の応答です。",
  "mode": "short",
  "provider": "mock"
}
```

### 入力エラー時にAPIが返すデータ

`text` が空文字 `""` で、`mode` が `short` のとき、APIは `422` を返す。

```json
{
  "error": {
    "code": "INVALID_INPUT",
    "message": "入力文章を確認してください。"
  }
}
```

### その他の要約エラー

| 状況 | APIが返すHTTPステータス |
|---|---|
| APIがLLMに接続できない、またはLLMから不正な応答が返った | `502` |
| APIはLLMに処理を依頼したが、制限時間内に応答が返らなかった | `504` |
| 外部LLMが利用回数などの上限に達した | `429` |
| APIの内部で想定外のエラーが起きた | `500` |

## APIの動作を確認する

- 確認先は `GET /health`。
- APIが応答できるときのHTTPステータスは `200`。

```json
{
  "status": "ok"
}
```
