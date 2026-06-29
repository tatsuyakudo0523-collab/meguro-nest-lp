# 目黒駅前ネスト整形外科 ｜ 自由診療LP（デプロイ用一式）

このフォルダは **そのまま公開できる静的サイト** です（ビルド不要）。
Claude Code は以下を実行して GitHub 作成 → push → Vercel デプロイまで行ってください。

## 構成
```
meguro-nest-lp/
├── index.html        # トップ（2つのLPへのリンク）
├── shiratama.html    # 白玉点滴LP（初回3,980円）
├── hirou.html        # 疲労回復点滴LP（初回2,480円）
├── support.js        # LPの実行ランタイム（編集不可・必須）
└── assets/           # 画像・ロゴ一式
```
- `shiratama.html` / `hirou.html` は `./support.js` と `assets/` に相対参照で依存。3つは同階層のまま配置すること。
- フレームワーク無し（Vercel の Framework Preset は **Other**）。ビルドコマンド・出力ディレクトリの設定は不要。

## 公開URL（デプロイ後）
- `/`            → トップ
- `/shiratama.html` → 白玉点滴LP
- `/hirou.html`     → 疲労回復点滴LP

---

## 手順A：GitHub CLI + Vercel CLI（推奨）

このフォルダ（`meguro-nest-lp/`）の中で実行：

```bash
# 1) Git 初期化 & コミット
git init
git add .
git commit -m "feat: 目黒ネスト整形外科 白玉/疲労回復 LP"
git branch -M main

# 2) GitHub リポジトリ作成 & push（gh CLI 使用）
gh repo create meguro-nest-lp --public --source=. --remote=origin --push
#   ※ private にする場合は --public を --private に

# 3) Vercel へデプロイ（vercel CLI 使用、フレームワーク Other＝設定不要）
vercel --prod --yes
```

`vercel` 未ログインなら `vercel login`、`gh` 未認証なら `gh auth login` を先に実行。

## 手順B：Vercel ダッシュボードで連携
1. 上記 1〜2 で GitHub に push。
2. Vercel → Add New → Project → このリポジトリを Import。
3. Framework Preset = **Other**、その他デフォルトのまま **Deploy**。

---

## 注意
- `support.js` は生成物のランタイム。**削除・改変しない**こと（消すとLPが描画されない）。
- 文言・価格・画像差し替えは `shiratama.html` / `hirou.html` 内を直接編集すれば反映。
- 配置先の想定：`OneDrive\Documents\GitHub\meguro-nest-lp`（既存の他LPと同じ並び）。
