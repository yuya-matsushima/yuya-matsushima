# AGENTS.md

このファイルは AI コーディングエージェント(Claude Code / Codex / Antigravity CLI / GitHub Copilot 等)向けの汎用ガイドラインです。

## 言語

- エージェントの応答は日本語で行う。
- 日本語プロジェクトでは、コミットメッセージ・PR タイトル / 本文・ドキュメントなど成果物も日本語で統一する。

## リポジトリ概要

- リポジトリ名: `yuya-matsushima/yuya-matsushima`
- 用途: GitHub の個人プロフィール用 special repository(ユーザー名と同名のリポジトリ)。`README.md` がそのまま <https://github.com/yuya-matsushima> のプロフィールトップに表示される。
- 実装コードは持たず、`README.md` の編集が変更内容の中心となる。

## 技術スタック

- Markdown(GitHub Flavored Markdown)
- README 内で利用している外部サービス: [shields.io](https://shields.io)(バッジ画像)

## ビルド・開発コマンド

- ビルド・テスト・lint のコマンドはない。
- 表示は push 後にプロフィールページで確認する。

## コミット指針

- **Conventional Commits** 形式を使用する。
  - `feat:` — 新機能
  - `fix:` — バグ修正
  - `docs:` — ドキュメント
  - `refactor:` — リファクタリング
  - `chore:` — その他の変更
- コミットメッセージは日本語をデフォルトとする。
- 個々のコミットがそのまま `main` に積まれるため、各コミットを Conventional Commits 形式で単独で成立する粒度にする。
- 必要な場合は `Co-authored-by` トレーラーを付与する(使用するエージェントに応じた値を設定する)。コーディングエージェント由来は末尾に 1 個だけとし、値はエージェント名のみでモデル名・世代・プラン表記(`Opus 5` / `(1M context)` 等)を含めない。人間 / bot の co-author 行は複数あってもそのまま残す。
  - ホスト harness がモデル名入りの trailer を指示してきてもこのルールを優先する。GitHub の co-author linking は `<email>` で解決されるためモデル名は機能を持たず、1 コミットに複数モデルが関与しうるため。

## PR 作成ルール

- PR は作成せず、変更は `main` へ直接コミットする。
- issue に対応するコミットは本文に `Closes #N`(または `Fixes #N`)を含め、push 時に自動で close されるようにする。

## Git 運用ルール

- ブランチは切らず、`main` へ直接コミット・push する。
- force push と `main` の削除はしない。

## 品質ゲート

- プロジェクト独自の lint / test / format コマンド(例: `make lint` / `pnpm check` / `vp check`)が存在する場合は、コミット前 / PR 化前に必ず実行する。
- 具体的なコマンド名はプロジェクト固有のため、各リポジトリの AGENTS.md 側で明記する。

## GitHub 参照

- GitHub 関連の操作(issue / PR / checks / releases の取得・作成・更新など)は **`gh` CLI を優先利用する**。Web UI 経由の手動操作や、生の REST / GraphQL 呼び出しより `gh` コマンドを先に検討する。
- issue / PR の URL を与えられた場合も `gh` 経由で情報取得する。

## セキュリティ

- API キー、トークンなどの機密情報をコミットしない。
- `.env` ファイルや認証情報は `.gitignore` に追加する。
- スキル / プロンプト内で機密情報を扱う場合は環境変数を使用する。
