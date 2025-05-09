# プロジェクト引き継ぎドキュメント

## プロジェクト概要

「docs-astro」は、複数のAstroプロジェクトをモノレポ構造で管理するドキュメントサイトです。主に英語の技術ドキュメントを日本語に翻訳したコンテンツを扱い、約20のプロジェクトを管理します。横断的な検索機能、多言語対応、ドキュメントのバージョン管理機能を備え、GitHub Pagesにデプロイします。

## 現在の進捗状況

### 完了したタスク

1. **モノレポの基本構造セットアップ**
   - pnpmワークスペースの設定（pnpm-workspace.yaml）
   - ルートpackage.jsonの設定
   - 基本ディレクトリ構造の作成（packages/, apps/, config/, scripts/）
   - .gitignoreの設定
   - READMEの更新

2. **共通設定の作成**
   - TypeScript設定（config/tsconfig/base.json, package.json, astro.json）
   - ESLint設定（config/eslint/base.js）
   - Prettier設定（.prettierrc）

3. **UI共通パッケージ**
   - パッケージ構造のセットアップ
   - 基本コンポーネントの作成
     - Button: 様々なスタイルとサイズのボタンコンポーネント
     - Card: タイトル、コンテンツ、フッターを持つカードコンポーネント
     - Navigation: ドロップダウンメニューをサポートするナビゲーションコンポーネント
     - Sidebar: ネストされたメニュー項目をサポートするサイドバーコンポーネント
     - Footer: リンクグループとソーシャルリンクをサポートするフッターコンポーネント
     - Alert: 情報、成功、警告、エラーの各種スタイルをサポートするアラートコンポーネント
   - TailwindCSSの設定

4. **テーマパッケージ**
   - カラーパレットの定義（ブランドカラー、テキスト、背景、ボーダー、ステータス）
   - タイポグラフィの設定（フォントファミリー、サイズ、ウェイト、行の高さ、文字間隔）
   - スペーシングとレイアウトの設定（スペーシング、コンテナ、ブレークポイント、z-index、ボーダー半径、シャドウ）
   - ダークモード対応（CSS変数とクラスベースの切り替え）

5. **i18nパッケージ**
   - 言語検出ユーティリティの作成
   - パス変換ユーティリティの作成
   - 翻訳ユーティリティの作成
   - 基本的な翻訳ファイル構造の設計

6. **検索パッケージ**
   - 検索コンポーネント（SearchBar, SearchResults）の作成
   - インデックス作成ユーティリティの実装
   - 検索ユーティリティの実装（ローカル検索、Algolia/MeiliSearch連携）

7. **バージョン管理パッケージ**
   - バージョン管理ユーティリティの作成
   - バージョン切り替えコンポーネント（VersionSelector）の実装
   - バージョン間差分表示機能（VersionDiff）の実装

### 次に取り組むべきタスク

1. **サンプルプロジェクトの作成（完了）**
   - ✅ Astroプロジェクトの作成
   - ✅ 基本的なディレクトリ構造の設定
   - ✅ TailwindCSSの設定
   - ✅ 多言語対応の基本構造（英語・日本語）
   - ✅ バージョン管理の基本構造（v1・v2）
   - ✅ サンプルコンテンツの作成（Getting Started）
   - ✅ コンポーネントの修正と実装
     - ✅ Buttonコンポーネントのリンク機能修正
     - ✅ Sidebarコンポーネントの項目表示機能修正
     - ✅ コードブロック表示の修正
   - ✅ スタイルシートの設定
   - ✅ 共有パッケージとの統合
   - ✅ 検索機能の実装

2. **GitHub Actionsの設定（完了）**
   - ✅ ビルドワークフローの作成
   - ✅ テストワークフローの作成
   - ✅ デプロイワークフローの作成

## 重要なコンポーネント

### 1. モノレポ構造

pnpmのワークスペース機能を活用して、以下の構造でプロジェクトを管理します：

- `packages/`: 共有パッケージ（UI、テーマ、i18n、検索、バージョン管理）
- `apps/`: 各ドキュメントプロジェクト
- `config/`: 共通設定
- `scripts/`: ユーティリティスクリプト

### 2. 共有パッケージ

各ドキュメントプロジェクト間で共有される機能を提供します：

- **UI**: 共通のUIコンポーネント
  - 現在、基本的なコンポーネント（Button, Card, Navigation, Sidebar, Footer, Alert）が実装済み
  - TailwindCSSを使用したスタイリング

- **テーマ**: 一貫したデザインシステム
  - カラーパレット、タイポグラフィ、スペーシング、レイアウトの定義
  - CSS変数を使用したテーマ設定
  - ダークモード対応

- **i18n**: 多言語対応ユーティリティ
  - 言語検出、パス変換、翻訳ユーティリティの実装
  - 英語と日本語の基本翻訳ファイル
- **検索**: 横断的な検索機能
  - 検索コンポーネント（SearchBar, SearchResults）
  - インデックス作成ユーティリティ
  - ローカル検索およびAlgolia/MeiliSearch連携
- **バージョン管理**: ドキュメントのバージョン管理機能
  - バージョン管理ユーティリティ
  - バージョン切り替えコンポーネント
  - バージョン間差分表示機能

### 3. ドキュメント構造

各ドキュメントプロジェクトは以下の構造を持ちます：

- 言語ごとのサブディレクトリ（`en/`, `ja/`など）
- バージョンごとのサブディレクトリ（`v1/`, `v2/`など）
- 動的ルーティングによるURLパス生成（`/[lang]/[version]/[...slug]`）

## 開発環境のセットアップ

### 前提条件

- Node.js 18以上
- pnpm 8以上
- Git

### セットアップ手順

1. リポジトリのクローン：
   ```bash
   git clone https://github.com/yourusername/docs-astro.git
   cd docs-astro
   ```

2. 依存関係のインストール：
   ```bash
   pnpm install
   ```

3. 開発サーバーの起動：
   ```bash
   # すべてのプロジェクトを起動
   pnpm dev
   
   # 特定のプロジェクトのみ起動
   pnpm --filter=@docs/project-name dev
   ```

## 新規プロジェクトの追加方法

1. 新しいAstroプロジェクトを作成：
   ```bash
   pnpm create astro apps/new-project --template minimal
   ```

2. 共有パッケージの依存関係を追加：
   ```bash
   pnpm --filter=@docs/new-project add @docs/ui @docs/theme @docs/i18n @docs/search
   ```

3. プロジェクト設定の調整：
   - `astro.config.mjs`の設定
   - 多言語対応の設定
   - バージョン管理の設定
   - 検索機能の設定

## デプロイ方法

GitHub Actionsを使用して自動デプロイを行います：

1. GitHub Pagesの設定：
   - リポジトリの設定からGitHub Pagesを有効化
   - デプロイソースとして「GitHub Actions」を選択

2. デプロイの実行：
   - mainブランチへのプッシュで自動的にデプロイが実行される
   - 手動でデプロイする場合はGitHub Actionsのワークフローを手動実行

## 翻訳ワークフロー

1. 原文（英語）ドキュメントの作成/更新
2. 翻訳が必要なファイルの抽出（`scripts/extract-translations.js`を使用）
3. 翻訳作業（手動または翻訳ツール支援）
4. 翻訳ファイルのレビューと修正
5. 翻訳ファイルのコミットとデプロイ

## トラブルシューティング

### よくある問題と解決策

1. **ビルドエラー**:
   - 依存関係が最新かどうか確認（`pnpm install`を実行）
   - TypeScriptエラーを確認（`pnpm lint`を実行）

2. **デプロイ失敗**:
   - GitHub Actionsのログを確認
   - ビルド出力が正しいパスに生成されているか確認

3. **検索機能の問題**:
   - 検索インデックスが正しく生成されているか確認
   - Algolia/MeiliSearchの設定を確認

## 今後の課題と改善点

1. **i18nパッケージの拡張**:
   - 言語切り替えUIコンポーネントの実装
   - 翻訳ファイル管理システムの構築
   - 追加言語のサポート

2. **検索機能の拡張**:
   - 検索エンジン（Algolia/MeiliSearch）との実際の連携
   - 検索UIの改善とカスタマイズ
   - 検索結果のフィルタリング機能の強化

3. **バージョン管理機能の拡張**:
   - バージョン間の差分表示機能の強化
   - 最新バージョンへの自動リダイレクト機能の実装
   - バージョン管理UIの改善

4. **サンプルプロジェクトの作成**:
   - 実際のドキュメントプロジェクトの作成
   - 共有パッケージの統合テスト

5. **CI/CDパイプラインの構築**:
   - GitHub Actionsによる自動ビルド・デプロイ
   - テスト自動化

## 最近の修正内容

### 不要なAstroファイルの削除（2025/5/9）

MDXコンテンツコレクションの実装に伴い、不要になったAstroファイルを削除しました。

削除内容：
1. 以下のAstroファイルを削除
   - `apps/sample-docs/src/pages/en/v1/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/en/v2/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/ja/v1/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/ja/v2/guide/getting-started.astro`

これらのファイルは、MDXファイルに移行され、動的ルーティングの実装（`apps/sample-docs/src/pages/[lang]/[version]/[...slug].astro`）によって表示されるようになったため、不要になりました。

### MDXコンテンツコレクションの実装（2025/5/9）

Astroのコンテンツコレクション機能を使用して、MDXファイルでドキュメントを管理できるように実装しました。

実装内容：
1. `apps/sample-docs/src/content/config.ts`を作成し、ドキュメントコレクションのスキーマを定義
   - タイトル、説明、公開日、更新日、著者、画像、タグ、ドラフトフラグ、順序、前後のページへのリンクなどのメタデータをサポート
2. サンプルMDXファイルの作成
   - `apps/sample-docs/src/content/docs/en/v1/guide/getting-started.mdx`
   - `apps/sample-docs/src/content/docs/ja/v1/guide/getting-started.mdx`
   - `apps/sample-docs/src/content/docs/en/v2/guide/getting-started.mdx`
   - `apps/sample-docs/src/content/docs/ja/v2/guide/getting-started.mdx`
3. 動的ルーティングの実装
   - `apps/sample-docs/src/pages/[lang]/[version]/[...slug].astro`を作成し、MDXコンテンツを表示
   - 目次の自動生成機能を追加
   - 前後のページへのナビゲーションリンクを実装
   - GitHubでの編集リンクを追加
4. インデックスページの更新
   - `apps/sample-docs/src/pages/en/v1/index.astro`
   - `apps/sample-docs/src/pages/en/v2/index.astro`
   - `apps/sample-docs/src/pages/ja/v1/index.astro`
   - `apps/sample-docs/src/pages/ja/v2/index.astro`
   - コンテンツコレクションからドキュメントのリストを取得して表示するように更新

これにより、MDXファイルを使用してドキュメントを管理できるようになり、フロントマターでメタデータを定義し、マークダウン記法でコンテンツを記述できるようになりました。また、コードブロックのシンタックスハイライトやインタラクティブなコンポーネントの埋め込みなど、MDXの機能を活用できるようになりました。

### GitHub Pagesのリダイレクト問題の修正（2025/5/9）

GitHub Pagesにデプロイされたサイト（https://dolphilia.github.io/docs-astro/）にアクセスした際に、
「Redirecting from / to /en/」と表示され、https://dolphilia.github.io/en/ に誤ってリダイレクトされる問題を修正しました。

修正内容：
1. `apps/sample-docs/astro.config.mjs`に`base: '/docs-astro'`を追加して、GitHub Pagesのサブディレクトリにデプロイする際のベースパスを設定
2. `apps/sample-docs/src/pages/index.astro`のリダイレクト先を絶対パス（/en）から相対パス（./en/）に変更

これにより、https://dolphilia.github.io/docs-astro/ にアクセスした際に、正しく https://dolphilia.github.io/docs-astro/en/ にリダイレクトされるようになりました。

### CSSファイルのパス問題の修正（2025/5/9）

GitHub Pagesにデプロイされたサイトで、CSSファイルのパスが正しく解決されず、スタイルが適用されない問題を修正しました。

修正内容：
1. 各ページのリンクパスにベースパス（`/docs-astro`）を追加
   - `apps/sample-docs/src/pages/en/index.astro`
   - `apps/sample-docs/src/pages/ja/index.astro`
   - `apps/sample-docs/src/pages/en/v1/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/en/v2/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/ja/v1/guide/getting-started.astro`
   - `apps/sample-docs/src/pages/ja/v2/guide/getting-started.astro`
2. LanguageSelectorコンポーネントのリンクパスを修正
   - `currentPath`からベースパスを削除してから`translatePath`関数に渡すように修正
3. VersionSelectorコンポーネントのリンクパスを修正
   - バージョン間の差分を表示するリンクのパスを修正

これにより、GitHub Pagesにデプロイされたサイトでもスタイルが正しく適用されるようになりました。
