# PROJECT_GUIDE

## 1. 目的 / 機能

Hiroki Inoue の個人 Web プロジェクト。以下 2 つの静的ページで構成される。

| ページ | 機能 |
|--------|------|
| **自己紹介サイト** (`index.html`) | Hero・About・Hobbies の 3 セクションで構成されたポートフォリオ（ダークテーマ） |
| **TODO アプリ** (`todo.html`) | タスクの追加・完了トグル・削除、3 種フィルター（すべて/未完了/完了済み）、localStorage 永続化（ライトテーマ） |

## 2. 主要ディレクトリと役割

```
my-first-project/
├── index.html         # ポートフォリオページ（HTML / CSS のみ）
├── todo.html          # TODO アプリ（HTML / CSS / Vanilla JS）
└── PROJECT_GUIDE.md   # 本ドキュメント
```

- フレームワーク・ビルドツールは未使用。すべて単一 HTML ファイルに CSS・JS をインラインで記述
- ディレクトリ分割なし（フラット構成）

## 3. 起動手順

ビルド不要。ブラウザで直接開くだけで動作する。

```bash
# macOS
open index.html
open todo.html

# Linux
xdg-open index.html

# または任意のブラウザで直接ファイルを開く
```

ローカルサーバーを使う場合:

```bash
# Python 3
python3 -m http.server 8000
# → http://localhost:8000 でアクセス
```

## 4. 依存関係

**外部依存なし。**

- パッケージマネージャー (`package.json`) 不使用
- CDN・外部ライブラリの読み込みなし
- HTML / CSS / Vanilla JavaScript のみで完結

## 5. 変更時の注意点

- **スタイルはすべてインライン `<style>`**: 外部 CSS ファイルは存在しない。変更は各 HTML 内の `<style>` ブロックを直接編集する
- **CSS 変数 (`:root`)**: 配色は `:root` のカスタムプロパティで一元管理されている。テーマ変更はここを起点にする
- **`todo.html` の localStorage キー**: `"todos"` 固定。キー名を変更すると既存データが失われる
- **XSS 対策**: TODO アプリはユーザー入力を `escapeHtml()` でサニタイズしている。入力表示箇所を追加する場合は同様にエスケープすること
- **レスポンシブ**: `clamp()` や `auto-fit` で対応済み。固定幅の追加はモバイル表示を壊す可能性がある
