# 目黒駅前ネスト整形外科 ｜ 自由診療LP（デプロイ用一式）

このフォルダは **そのまま公開できる静的サイト** です（ビルド不要）。
今回 **3枚目（表情ジワ・エラ注入LP）を追加** しました。既存リポジトリの更新 → push → Vercel 再デプロイまで行ってください。

## 構成
```
meguro-nest-lp/
├── index.html        # トップ（3つのLPへのリンク）
├── shiratama.html    # 白玉点滴LP（初回3,980円）
├── hirou.html        # 疲労回復点滴LP（初回2,480円）
├── chunyu.html       # 表情ジワ・エラ注入LP（1部位 初回5,000円）← 今回追加
├── support.js        # LPの実行ランタイム（編集不可・必須）
└── assets/           # 画像・ロゴ一式（c-*.png を追加）
```
- 各HTMLは `./support.js` と `assets/` に相対参照で依存。同階層のまま配置すること。
- フレームワーク無し（Vercel の Framework Preset は **Other**）。ビルド設定不要。

## 公開URL（デプロイ後）
- `/`            → トップ
- `/shiratama.html` → 白玉点滴LP
- `/hirou.html`     → 疲労回復点滴LP
- `/chunyu.html`    → 表情ジワ・エラ注入LP

---

## 手順A：既存リポジトリを更新して再デプロイ（推奨）

すでに 1・2枚目を push 済みのリポジトリがある前提。このフォルダの中身で上書きし、差分を push：

```bash
# 既存リポジトリのフォルダ内で（このzipの中身を上書きコピー後）
git add .
git commit -m "feat: 表情ジワ・エラ注入LP(chunyu) を追加・トップ更新"
git push

# Vercel は GitHub 連携済みなら push で自動再デプロイ。
# 手動でやる場合は CLI:
vercel --prod --yes
```

## 手順B：まだリポジトリが無い場合（新規作成）

このフォルダ（`meguro-nest-lp/`）の中で実行：

```bash
git init
git add .
git commit -m "feat: 目黒ネスト整形外科 LP 3枚（白玉/疲労回復/表情ジワ）"
git branch -M main
gh repo create meguro-nest-lp --public --source=. --remote=origin --push   # private なら --private
vercel --prod --yes
```

`vercel` 未ログインなら `vercel login`、`gh` 未認証なら `gh auth login` を先に実行。
Vercel ダッシュボード派：Add New → Project → リポジトリを Import → Framework **Other** → Deploy。

---

## 注意
- `support.js` は生成物のランタイム。**削除・改変しない**こと（消すとLPが描画されない）。
- 文言・価格・画像差し替えは各HTML（`shiratama.html` / `hirou.html` / `chunyu.html`）内を直接編集すれば反映。
- 配置先の想定：`OneDrive\Documents\GitHub\meguro-nest-lp`。
- 3枚目は薬剤の固有商品名を出さず、医療広告ガイドラインの限定解除要件（未承認である旨・入手経路・国内承認品の有無）を「薬剤について」に記載済み。
