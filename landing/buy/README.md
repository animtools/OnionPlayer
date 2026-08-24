# 購入ドア（安定 URL）

OnionPlayer のリリースリポ（未作成）の `landing/buy/` に置く。GitHub Pages での想定 URL:

- 買い切り: `https://animtools.github.io/<repo>/landing/buy/perpetual.html`
- サブスク: `https://animtools.github.io/<repo>/landing/buy/subscribe.html`

アプリ側の `.env`:

```env
BUNDLED_LANDING_PUBLIC_ORIGIN=https://animtools.github.io/<repo>/landing
```

→ アプリは `{ORIGIN}/buy/perpetual.html` / `{ORIGIN}/buy/subscribe.html` を開く。

## 重要

- **出荷済みビルドがこの URL を参照するため、パスを変えない・削除しない。**
- **現在この2枚は「準備中」ページ**で、checkout へは飛ばさない。
  OnionPlayer は test 段階で、購入導線の公開は launch ゲートのため
  （`biz-cycle-hub/playbooks/stages.md` / ADR 0001）。
- 実際の Polar checkout URL は、launch 時に各 HTML のコメントに記録したうえで
  `meta refresh` + `location.replace` へ戻す。

## 未完了（launch 前の作業）

1. リリースリポを作成し、この `landing/` を配置して GitHub Pages を有効にする
2. `.env` の `BUNDLED_LANDING_PUBLIC_ORIGIN` **だけ**を埋めて**再ビルド**する
   （origin があれば `BUNDLED_LICENSE_PURCHASE_URL*` は無視される実装。
   **生の Polar URL は焼かない** — 焼くと価格改定のたびに配布済みビルドの導線が死ぬ）
3. 再ビルド後、**課金ゲートのダイアログを撮り直す**
   （現ビルドは購入 URL が空のため「（購入 URL は未設定です）」が出る。
   record-for-ai 票02 の「撮り直しが必要になるショット」を参照）
