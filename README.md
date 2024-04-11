# StreamlitSampleApp240101
# StreamlitとGoogle検索の統合

このStreamlitアプリケーションは、Googleカスタム検索エンジン（CSE）をGoogle BigQueryと統合して検索を実行し、結果を分析用に保存する方法を示しています。研究者、マーケター、データアナリストなど、時間を追ってウェブ検索結果を追跡・分析する必要がある人にとって強力なツールです。

## 機能

- **Google CSEを通じたウェブ検索**: アプリから直接ウェブ検索を実行します。
- **結果の保存**: 検索結果をGoogle BigQueryに自動的に保存し、さらなる分析が可能です。
- **Streamlit UI**: Streamlitを使用した使いやすいインターフェイスで、迅速なデプロイと共有が可能です。

## 前提条件

開始する前に、以下が必要です:
- Google Cloud Platform（GCP）アカウント。
- GCPにおいてBigQueryとCustom Search Engine APIが有効になっているプロジェクト。
- 特定の検索要件に合わせて設定されたカスタム検索エンジン（CSE）。
- GCPサービスへのプログラムによるアクセス用のサービスアカウントキー。

## 設定手順

### 1. 環境設定

リポジトリをローカルマシンにクローンし、プロジェクトディレクトリに移動します。仮想環境を作成し、有効にします:

```bash
python -m venv venv
source venv/bin/activate  # Windowsでは `venv\Scripts\activate`
pip install -r requirements.txt
```

### 2. Google Cloudの設定
Google Cloudコンソールに移動し、新しいプロジェクトを作成するか、既存のプロジェクトを選択します。
プロジェクトにBigQuery APIとCustom Search Engine APIを有効にします。
カスタム検索エンジンを作成し、CSE IDをメモします。
IAM & 管理セクションでサービスアカウントを作成し、JSONキーファイルをダウンロードし、BigQueryとCustom Searchへのアクセス用のロールを設定します。
### 3. 設定
Google APIキー、CSE ID、BigQueryデータセット情報をローカル開発用に.envファイルに保存するか、デプロイ用にStreamlit Secretsを使用します。
.envファイルの例:
```bash
BIGQUERY_PROJECT_ID=あなたのプロジェクトID
BIGQUERY_DATASET_NAME=あなたのデータセット名
BIGQUERY_TABLE_NAME=あなたのテーブル名
GOOGLE_API_KEY=あなたのAPIキー
GOOGLE_CSE_ID=あなたのCSE_ID
```
スクリプト内のservice_account_file_path変数を、ダウンロードしたサービスアカウントJSONキーファイルのパスに更新します。
### 4. アプリの実行
Streamlitアプリを開始します:
```bash
streamlit run スクリプト名.py
表示されたURLに移動して、アプリケーションとのやり取りを開始します。
```

## 使用方法
提供されたテキストボックスに検索クエリを入力し、「検索」ボタンをクリックします。
検索ボックスの下に検索結果が表示されます。
結果はクエリ、タイムスタンプ、その他のメタデータと共に指定されたBigQueryテーブルに自動的に挿入されます。
## 貢献
このプロジェクトを強化するための貢献を歓迎します。リポジトリをフォークして、変更を含むプルリクエストを送信してください。

## ライセンス
プロジェクトがリリースされているライセンスを指定します。
