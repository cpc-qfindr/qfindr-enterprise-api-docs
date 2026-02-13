# QFINDR Enterprise API

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cpc-qfindr/qfindr-enterprise-api-docs/blob/master/QFINDR_API_Getting_Started.ipynb)


本リポジトリでは、企業情報リサーチツール[QFINDR](https://qfindr.jp/?utm_source=api_docs&utm_medium=github)の**QFINDR Enterpriseプラン** の一部機能として提供している企業情報取得APIの概要と、クイックスタートガイドおよびQFINDR MCP([MCP (Model Context Protocol)](https://modelcontextprotocol.io/))サービスの概要を掲載しています。


## 🏢 QFINDR Enterprise APIについて

QFINDR Enterprise APIを利用することで、貴社で既にご利用中の基幹システム、CRM、BIツール、あるいは独自の社内ワークフローと当サービスをシームレスに統合できます。

### 主な活用シーン
- **データ連携**: 既存の顧客データベース等の情報補完
- **独自UIの構築**: 社内ツールへの機能埋め込み
- **分析の高度化**: QFINER内のデータを統合して独自のBIツールで解析

---

## 🚀 APIの利用イメージ（クイックスタート）

「実際にどのようにコードを記述するのか」「どのようなデータが返ってくるのか」をすぐにご確認いただけるよう、Google Colab上で動作するサンプルコードを用意しています。

以下のボタンをクリックすると、ブラウザ上で直接Pythonコードを実行してAPIの挙動を体験いただけます。  

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cpc-qfindr/qfindr-enterprise-api-docs/blob/master/QFINDR_API_Getting_Started.ipynb)

> [!NOTE]
> サンプルの実行にはデモ用のAPIキー、または評価用アカウントが必要です。

---

## 📩 利用開始のお手続き

QFINDR APIは、エンタープライズ向けプランをご契約のお客様にご提供しております。  
利用をご希望の場合や、仕様の詳細、お見積りについては、以下のWebサイトよりフリートライアルをお申し込みください。

**[QFINDRフリートライアルの申込み](https://qfindr.jp/contact?utm_source=api_docs&utm_medium=github)**

### 導入までの流れ
1. **お問い合わせ**: 上記リンクより必要事項をご記入ください。
2. **ヒアリング・ご提案**: 貴社のユースケースに合わせた最適な連携方法をご提案します。
3. **サンドボックス提供**: 開発・検証用のテスト環境を発行いたします。
4. **本番利用開始**: 本番用APIキーを発行し、実運用を開始いただけます。

## 🤖 QFINDR MCPサービスについて

QFINDR Enterprise APIを利用し、外部の生成AIと連携するためのMCPサービスを提供しています。

> [!TIP]
> MCPは[Model Context Protocol](https://modelcontextprotocol.io/)の略で、LLMが外部ツールやデータソースと連携するためのプロトコルです。

### 👉 QFINDR MCPサービスの活用イメージ

外部生成AIサービス(Claude、Claude Desktop、ChatGPT、Copilot Studio、VSCode等)と連携し、自然言語処理での企業検索や企業分析を可能にします。

> [!TIP]
> MCPサービスの利用には、QFINDR Enterpriseプランの契約もしくはProプランでのオプション契約が必要です。

> [!TIP]
> 外部生成AIサービスはお客様ご自身での契約・準備が必要となります。

> [!WARNING]
> MCPサービス経由でQFINDR Enterprise APIへのアクセスが発生した場合には、アクセストークン毎に取得企業数が通常通り加算され、上限に達した場合は接続が制限されます。

#### ① 企業検索/企業リストの作成

プロンプト例：

```
QFINDRで群馬県の企業で売上高20億円以下(推定含む)で、設立が浅い企業で水の浄化関連の装置を作っているような会社のリストを出したい。ある場合は、QFINDRの検索ページへのURLも併記して。
```

結果例：

```
検索結果が見つかりました。群馬県で売上高20億円以下(推定含む)、設立が浅く、水の浄化関連装置を製造している企業を中心に12社が該当しました。該当企業リスト特に装置製造に該当する主要な3社:

株式会社YYYYYY

法人番号: 9070001111111
業種: 計測器・分析器・試験機製造業
概要: 排ガス・排液の浄化装置や脱臭・消臭装置、水質浄化装置の開発・製造・販売
URL: http://www.yyyyyy.com/
...
```

> [!TIP]
> リスト作成の場合は自動でlimit句が利用されます。すべての結果を閲覧したい場合は検索ページへのURLからQFINDRにてご確認をお願いします。

#### ② 類似企業検索

プロンプト例：

```
株式会社クレジット・プライシング・コーポレーション(https://www.credit-pricing.com/)の類似企業を金融リスクモデリングの観点でQFINDRで探してください。ある場合は、QFINDRの検索ページへのURLも併記して。
```

結果例：

```
株式会社クレジット・プライシング・コーポレーション(CPC)の類似企業を金融リスクモデリングの観点から探すため、まずCPCの事業内容を確認してから、QFINDRで検索します。

...

株式会社クレジット・プライシング・コーポレーション(CPC)の類似企業

株式会社XXXXX

信用リスク評価のモデル開発、シミュレーションツール提供
気候変動シナリオ分析、マクロ・ストレス・テスト

...
```

#### ③ 企業分析


### ⚙️ MCPサービスの設定方法

> [!WARNING]
> MCPサービスのご利用には、QFINDR Enterprise APIのAPIトークンが必要となります。QFINDRのアカウントページにてAPIトークンをご確認ください。

各生成AIサービスによって設定方法が異なります。

<details><summary>Claude Desktop の場合</summary>

`claude_desktop_config.json` の設定例:

**Mac / Linux:**

```json
{
  "mcpServers": {
    "qfindr-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://qfindr.jp/mcp",
        "--header",
        "Authorization: Bearer YOUR_API_TOKEN"
      ]
    }
  }
}
```

**Windows:**

Windowsでは `npx` のパス解決でエラー（`C:\Program` ...）が発生する場合があるため、`cmd`経由での実行を推奨します。

```json
{
  "mcpServers": {
    "qfindr-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "mcp-remote",
        "https://qfindr.jp/mcp",
        "--header",
        "Authorization: Bearer YOUR_API_TOKEN_HERE"
      ]
    }
  }
}
```

> [!TIP]
> npxの利用のため、node.jsのインストールが必要となります。

node.jsのインストール方法(windowsの場合)：

```powershell
> winget install -e --id OpenJS.NodeJS.LTS

> Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force
```

</details>


<details><summary>Claude(Web版)の場合</summary>

> [!WARNING]
> Claude(Web版)では、無料版ではMCP機能は提供されておりません。Claude Pro以上で利用可能です。

ブラウザにてClaudeにログインを行い、「設定」→「コネクタ」→「カスタムコネクタ」にて、下記の通り設定を行ってください。

|項目|値|
|:---|:---|
|名前|qfindr-mcp|
|リモートMCPサーバURL|https://qfindr.jp/mcp?token=YOUR_API_TOKEN|
|詳細設定(OAuth ClientID) | 空欄 |
|詳細設定(OAuthクライアントシークレット) | 空欄|

</details>

<details><summary>ChatGPTの場合</summary>

> [!WARNING]
> ChatGPTでは、無料版ではMCP機能は提供されておりません。ChatGPT Plus以上で利用可能です。

ブラウザにてChatGPTにログインを行い、「設定」→「アプリ」にて、下記の通り設定を行ってください。

* 「高度な設定」の項目より、「開発者モード」をONにしてください。

その後、「アプリを作成する」より下記の通り設定を行ってください。

|項目|値|
|:---|:---|
|名前|qfindr-mcp|
|MCPサーバのURL|https://qfindr.jp/mcp?token=YOUR_API_TOKEN|
|認証 | 認証なし |

</details>


<details><summary>Copilot Studioの場合</summary>

ログイン後、「エージェント」より新しいエージェントを作成します。
作成したエージェントの「ツール」タブより「ツールを追加する」を選択します。
新規作成より「モデルコンテキストプロトコル」を選択します。

|項目|値|
|:---|:---|
|サーバー名|qfindr-mcp|
|サーバーの記述|QFINDRを用いて企業検索や企業分析を行うためのAPIを利用するためのMCPサーバ|
|サーバーのURL|https://qfindr.jp/mcp|
|認証|APIキー|
|タイプ|ヘッダー|
|ヘッダー名|Authorization|
|ヘッダーの値|Bearer YOUR_API_TOKEN|

> [!TIP]
> ヘッダーの値は上記画面での設定ではなく、その後の「接続」段階で設定します。
> 「新しい接続を作成」にて遷移した画面に入力をします。

> [!TIP]
> 「接続マネージャ」で当該MCPサーバへの接続を行ってください。


</details>

### ☑️ 動作テスト

MCPサービスの設定が正しくされているか、は以下プロンプトにてご確認ください。

#### MCPサーバの設定の確認

```
QFINDRで使えるtool一覧を教えて。
```

🎉返答例：

```
QFINDRのツール一覧は、以下の通りです。

企業情報検索API（企業の基本情報、財務情報、関係者情報などの検索）
企業情報検索件数取得API（企業検索のヒット件数取得）
業種一覧取得API（大業種の一覧取得）
...
```

#### QFINDR APIが利用できるかの確認

```
QFINDRのAPIトークンを教えて。
```

🎉返答例：

```
QFINDRのAPIキー情報

トークン：[ご自身のAPIトークン]
作成日時：2025年6月24日 11:38（JST）
...
```

### 👀 Tips

> [!TIP]
> MCPサービスの活用事例などについての情報を更新予定です。



---
© 2026 QFINDR . All rights reserved.