# 購入ドア（安定 URL）

このリポの `landing/buy/` に置く2枚。GitHub Pages での URL:

- 買い切り: `https://animtools.github.io/OnionPlayer/landing/buy/perpetual.html`
- サブスク: `https://animtools.github.io/OnionPlayer/landing/buy/subscribe.html`

アプリ側のビルド設定:

```env
BUNDLED_LANDING_PUBLIC_ORIGIN=https://animtools.github.io/OnionPlayer/landing
```

→ アプリは `{ORIGIN}/buy/perpetual.html` / `{ORIGIN}/buy/subscribe.html` を開く。

## 重要

- **出荷済みビルドがこの URL を参照するため、パスを変えない・削除しない。**
- **現在この2枚は「準備中」ページ**で、checkout へは飛ばさない。
  OnionPlayer は test 段階で、購入導線の公開はまだ先のため。
- 実際の checkout URL は、公開時に各 HTML のコメントに記録したうえで
  `meta refresh` + `location.replace` へ戻す。

## 未完了（購入導線の公開前）

1. checkout URL を各 HTML に入れ、案内ページから転送へ戻す
2. **生の checkout URL はアプリに焼かない** — 焼くと価格改定のたびに
   配布済みビルドの導線が死ぬ。アプリが持つのは上の origin 1本だけ
3. 課金ゲートのダイアログのスクリーンショットを撮り直す
