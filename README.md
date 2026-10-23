# Local RAG

Ollama、Streamlit、ChromaDBを使って、Word文書（`.docx`）の内容を検索しながらローカルLLMと会話するアプリです。

## セットアップ

PythonとOllamaが必要です。次のコマンドでPythonの仮想環境を作成し、依存ライブラリをインストールします。

```sh
python3 -m venv myvenv
source myvenv/bin/activate
pip install -r requirements.txt
```

Ollamaに必要なモデルを用意します。

```sh
ollama pull llama3.1:8b
ollama pull nomic-embed-text
```

このアプリの接続先は `http://localhost:2000` です。Ollamaをそのポートで起動してください。すでに起動している場合は停止してから実行します。

```sh
OLLAMA_HOST=127.0.0.1:2000 ollama serve
```

別のターミナルで仮想環境を有効にしてアプリを起動します。

```sh
source myvenv/bin/activate
streamlit run local_RAG.py
```

## 使い方

1. サイドバーからWord文書をアップロードします。
2. 「インデックス作成」を押します。
3. チャット欄に文書についての質問を入力します。

モデル名、temperature、システムプロンプトはサイドバーで変更できます。

## ローカルデータ

文書の本文と埋め込みベクトルは `chroma_db/` に保存されます。このフォルダと仮想環境、認証情報は `.gitignore` で公開対象から除外しています。
