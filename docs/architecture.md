# AI Knowledge Studio 基本設計

[画面（React）] → [API（FastAPI）] → [要約Service] → [Provider]

## 短い要約を頼んだときの流れ

1. 画面は、入力された文章と要約モード `short` をAPIに送る。
2. APIは、文章の前後の空白を除き、本文が 1〜5000文字 で、モードが short または detailed かを確認する。条件を満たせば、本文とモードを要約Serviceに渡す。
3. 要約Serviceは、モードに合わせて「短く要約してください」という指示を作り、Providerに渡す。
4. 公開デモでは Mock Provider がデモ用の結果を返す。ローカルで実LLMを使うときは Ollama Provider がOllamaに要約を依頼する。
5. 結果は Provider → 要約Service → API（FastAPI） → 画面（React） の順に戻り、画面に要約とProviderの種類が表示される。