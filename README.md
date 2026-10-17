# ひとさじBot サイト

Spoon のボット「ひとさじBot」の紹介サイトです。ボットの紹介と、ボット全体および各アプリのプライバシーポリシーを載せます。

- 公開先: Cloudflare Pages（`https://hitosaji.live`。`https://www.hitosaji.live` からは Cloudflare の Redirect Rules で 301 転送）
- 作り方: HTML と CSS だけ。ビルドの仕組みと JavaScript は使いません。外部の CDN やアクセス解析も使いません。

## フォルダの構成

公開するのは `public/` の中だけです。README などリポジトリ直下のファイルは公開されません。

| パス | URL | 内容 |
|---|---|---|
| `public/index.html` | `/` | ひとさじBot の紹介、アプリの一覧、連絡先 |
| `public/privacy.html` | `/privacy` | ボット全体のプライバシーポリシー |
| `public/manager/index.html` | `/manager/` | ひとさじマネージャーの紹介 |
| `public/manager/privacy.html` | `/manager/privacy` | ひとさじマネージャーのプライバシーポリシー |
| `public/manager/terms.html` | `/manager/terms` | ひとさじマネージャーの利用規約 |
| `public/terms.html` | `/terms` | ボット全体とこのサイトの利用規約 |
| `public/lens/index.html` | `/lens/` | Listener Lens の紹介 |
| `public/lens/privacy.html` | `/lens/privacy` | Listener Lens のプライバシーポリシー |
| `public/404.html` | 見つからないとき | Cloudflare Pages が自動で使います |
| `public/assets/` | `/assets/` | 共通の CSS とファビコン |
| `public/_headers` | — | セキュリティのヘッダー（CSP など） |

Cloudflare Pages は `.html` を省いた URL で配信し、`/privacy.html` へのアクセスは `/privacy` へ転送します。

ヘッダー、ナビゲーション、フッターは各ページに直接書いています。変えるときは全ページを直してください。

## Cloudflare Pages の設定

| 項目 | 値 |
|---|---|
| Framework preset | None |
| Build command | （空欄） |
| Build output directory | `public` |

## 手元での確認

`.html` を省いた URL や `_headers` まで確かめるには、Wrangler を使います。

```sh
npx wrangler pages dev public
```

見た目だけなら、`public/index.html` をブラウザで開いても確認できます（CSS は `/assets/` の絶対パスなので、`npx serve public` などで配信してください）。

## 変更するときの注意

- **Lens のポリシー**: `/lens/privacy` の保存期間などの値は、`lens/docs/spoon-developers-spec.md` の §6.3 と一致させてください。どちらかを変えたら、もう一方も確認します。改定したら、ページの改定日も更新します。
- **ひとさじマネージャーのポリシー**: `/manager/privacy` の保存期間などの値は、`manager/docs/spec.md` の §4 と一致させてください。審査の内容（`manager/docs/spoon-app-registration.md`）とも食い違わないようにします。
- **連絡先**: `contact@hitosaji.live` と X の `@sp_shino04` を使います。変えるときは、全ページと Spoon のボットのプロフィールを直してください。
- **書かないこと**: 実名、Spoon 公式のサービスだと誤解される書き方、まだない機能、Lens の利用の呼びかけ。
