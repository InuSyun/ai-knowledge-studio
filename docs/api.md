# AI Knowledge Studio API仕様

## 要約する

- 送信先: `POST /api/v1/summaries`

### 画面からAPIに送るデータ

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