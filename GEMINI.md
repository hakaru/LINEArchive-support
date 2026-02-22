# ChatArchive Support Site

## プロジェクト概要
ChatArchive（macOS用チャット履歴バックアップ・閲覧アプリ）の公式サポートサイト。
GitHub Pages で静的ホスティング。ビルドツールなし、HTML/CSS のみ。

## 技術スタック
- 静的 HTML + CSS（フレームワーク不使用）
- GitHub Pages（main ブランチから自動デプロイ: `.github/workflows/pages.yml`）
- Google Analytics（G-7NHBDYBWEY）

## ディレクトリ構成
```
/                     … 日本語メインページ（デフォルト言語）
├── css/
│   ├── style.css     … サイト共通スタイル
│   └── blog.css      … ブログ専用スタイル
├── blog/             … 日本語ブログ記事
├── en/               … 英語版
│   ├── index.html
│   └── blog/
├── th/               … タイ語版
│   ├── index.html
│   └── blog/
├── zh-Hant/          … 繁体中国語版
│   ├── index.html
│   └── blog/
├── images/           … アイコン画像
├── privacy.html      … プライバシーポリシー（日本語）
├── terms.html        … 利用規約（日本語）
├── favicon.svg
└── .github/workflows/pages.yml
```

## 多言語対応
- 対応言語: ja（デフォルト）, en, th, zh-Hant
- ルート `index.html` に `navigator.language` ベースの自動リダイレクト
- 各言語ディレクトリは独立した HTML ファイル（テンプレートエンジン不使用）
- アセットパス規則:
  - ルート: `css/style.css`, `favicon.svg`
  - `{lang}/`: `../css/style.css`, `../favicon.svg`
  - `{lang}/blog/`: `../../css/style.css`, `../../css/blog.css`, `../../favicon.svg`

## ブログ記事（各言語共通の3記事）
1. `chatarchive-getting-started.html` — ChatArchive 使い方ガイド
2. `line-backup-notebooklm.html` — LINE トーク履歴 × NotebookLM AI 分析
3. `line-export-all-chats.html` — LINE 全チャット一括エクスポート

## レビュー時の注意点
- ビルドステップがないため、HTML/CSS の変更は直接本番に反映される
- 外部 JS ライブラリ不使用（nav toggle のインライン JS のみ）
- LemonSqueezy の決済 URL はハードコードされている（変更不可）
- 各言語ファイルは独立しているため、構造変更時は全言語に反映が必要
- `lang` 属性が各ファイルの `<html>` タグで正しく設定されていることを確認
