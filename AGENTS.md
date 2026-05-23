# AGENTS.md

このファイルは AI コーディングエージェント（Claude Code / Codex / Gemini CLI / GitHub Copilot 等）向けの汎用ガイドラインです。

## 言語

- エージェントの応答は日本語で行う。
- 日本語プロジェクトでは、コミットメッセージ・PR タイトル / 本文・ドキュメントなど成果物も日本語で統一する。

## リポジトリ概要

- リポジトリ名: `yuya-matsushima/yuya-matsushima`
- 用途: GitHub の個人プロフィール用 special repository（ユーザー名と同名のリポジトリ）。`README.md` がそのまま <https://github.com/yuya-matsushima> のプロフィールトップに表示される。
- 実装コードは持たず、`README.md` の編集が変更内容の中心となる。

## 技術スタック

- README 内で利用している外部サービス: [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)（統計バッジ画像）

## コミット指針

- **Conventional Commits** 形式を使用する。
  - `feat:` — 新機能
  - `fix:` — バグ修正
  - `docs:` — ドキュメント
  - `refactor:` — リファクタリング
  - `chore:` — その他の変更
- コミットメッセージは日本語をデフォルトとする。
- コミット粒度は細かくて良い。PR は squash-and-merge で単一コミットに丸められる前提のため、PR 単位で成立していれば良い。
- 必要な場合は `Co-authored-by` トレーラーを末尾に付与する（使用するエージェントに応じた値を設定する）。

## PR 作成ルール

- PR タイトルも **Conventional Commits** 形式に寄せる（squash-and-merge 後のコミットメッセージがそのまま PR タイトルになるため）。
- issue 駆動の PR は本文に `Closes #N`（または `Fixes #N`）を必ず含め、マージ時に自動で close されるようにする。
- マージ方式は **squash-and-merge** をデフォルトとする。
- **1 PR = 1 目的**。1 つの PR で複数の論点を混ぜない。

## Git 運用ルール

- ブランチモデルは **GitHub Flow** を採用する（`main` は常時デプロイ可能に保ち、機能開発はブランチ + PR で進める）。
- 何らかの変更を加える場合は**必ず**ブランチを切ってから作業を開始する（`main` 上での直接コミット・直接 push は禁止）。
- ブランチ命名規則は Conventional prefix + slug とする。
  - `feat/` — 新機能追加
  - `fix/` — バグ修正
  - `docs/` — ドキュメント更新
  - `refactor/` — リファクタリング
  - `chore/` — その他の変更
- issue ベースで開発する場合はブランチ名に issue 番号を含める（例: `feat/136-agents-base-md`）。issue が無い ad-hoc な作業では issue 番号を省略して `<type>/<slug>` とする。

## GitHub 参照

- GitHub 関連の操作（issue / PR / checks / releases の取得・作成・更新など）は **`gh` CLI を優先利用する**。Web UI 経由の手動操作や、生の REST / GraphQL 呼び出しより `gh` コマンドを先に検討する。
- issue / PR の URL を与えられた場合も `gh` 経由で情報取得する。

