# AI Knowledge Studio

技術書・論文・学習メモから抜き出した文章を要約し、内容の理解を助けるWebアプリです。
利用者は「短い要約」と「詳しい要約」を選べます。

## 開発状況

Week 1の設計資料を作成しています。

## 動作方針

- ローカルでは、Ollama Provider を使って実LLMによる要約を試します。
- 公開デモでは、Mock Provider に固定してデモ用の結果を表示します。

## 設計資料

- [要件定義](docs/requirements.md)
- [基本設計](docs/architecture.md)
- [API仕様](docs/api.md)
- [設計判断の記録（ADR）](docs/adr/)