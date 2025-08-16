# ar-pins-sample

最小構成の Web AR デモです。A-Frame + AR.js を使ったマーカー型 AR（HIRO マーカー）で、GLTF（Duck.glb）を表示し、読み込み失敗時は回転するボックスにフォールバックします。画面右下の📷ボタンでスクリーンショットを保存できます。

## 必要要件
- Node.js（LTS 推奨）
- パッケージマネージャ: `pnpm` または `npm`

## ローカル起動
```bash
pnpm dev        # もしくは: npm run dev
```
ブラウザが自動で開き、`http://localhost:3000` で配信されます。カメラアクセスを許可してください。

## 使い方
1. HIRO マーカーを画面に表示するか、紙に印刷して用意します。
2. ページを開き、カメラをマーカーに向けます。
3. アヒルのモデルが表示されます（読み込み失敗時はボックス）。
4. 右下の📷ボタンでスクリーンショットを保存できます。

モデルを差し替える場合は `index.html` 内の `<a-assets>` で `a-asset-item` の `src` を変更してください。ローカルファイルを追加する場合は `assets/` フォルダを作成して配置し、相対パスで参照します。

## プロジェクト構成
- `public/index.html`: エントリーポイント（HTML/JS/CSS 最小限）
- `package.json`: 開発サーバ用スクリプト（`pnpm dev`）
- `AGENTS.md`: コントリビュートガイドライン

## デプロイ
ビルド工程は不要です。任意の静的ホスティング（GitHub Pages / Netlify など）に `public/` を配信してください。カメラ利用のため本番は HTTPS を必須とし、外部アセットも HTTPS で読み込んでください。

### Cloudflare Workers
Wrangler で静的アセットとして配信できます。
```bash
# 初回のみ
pnpm dlx wrangler login

# ローカルプレビュー
pnpm run cf:dev

# デプロイ（*.workers.dev に公開）
pnpm run cf:deploy
```

## トラブルシューティング
- カメラが起動しない: ブラウザの権限を許可、HTTPS/localhost でアクセス。
- マーカーを認識しない: 明るい環境で、マーカー全体がフレームに入るよう調整。
- モデルが表示されない: コンソールのエラー確認。CORS/パスの誤りや CDN 停止をチェック。
