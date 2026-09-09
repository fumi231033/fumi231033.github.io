# 送料チェッカー公開ページ

このフォルダーは、非公開のアプリ本体とは分離して公開する静的ページ一式です。固定費0円のGitHubユーザーサイト[https://fumi231033.github.io/](https://fumi231033.github.io/)で公開しています。

## 生成

`app/`で次を実行します。

```powershell
npm run generate:privacy-policy
npm run generate:public-site
```

ポリシー本文は`app/data/privacy_policy.json`、公開サイト設定は`app/data/public_site.json`を原本とします。生成後は`npm test`に加え、次の公開専用検査を実行します。

```powershell
npm run check:public-site-release
```

この検査は原本とHTMLの一致、必須ファイル、HTTPS URL、内部リンク、許可した問い合わせ先、秘密情報候補、問い合わせ時の個人情報警告を確認します。初回版へ広告用`app-ads.txt`が誤って含まれた場合も失敗します。

## 公開・更新手順

公開リポジトリは`fumi231033/fumi231033.github.io`、公開元は`main`ブランチのルートです。GitHub Issuesを有効化し、GitHub PagesはHTTPSを強制しています。

1. 原本を更新し、公開ファイルを再生成する
2. `npm run check:public-site-release`を実行する
3. このフォルダーの6ファイルだけを公開リポジトリのルートへ反映する
4. 差分と秘密情報の非混入を確認して`main`へプッシュする
5. ログアウト状態でトップ、プライバシーポリシー、問い合わせページ、Issueフォームを確認する
6. `app/`で`npm run check:public-web-endpoints`を実行する

初回公開は2026-09-10に完了し、プライバシーポリシーと問い合わせページがHTTPS・HTTP 200で利用できることを確認しました。

## `app-ads.txt`について

初回公開版では広告SDKを使用しないため、`app-ads.txt`はまだ置きません。将来AdMobを導入する場合に、AdMobから取得した正式な1行を改変せず、このフォルダーのルートへ`app-ads.txt`として追加します。Publisher IDや広告ユニットIDの推測値・仮値は公開しません。

公開ページ、Issue、コミットへ、利用者の氏名、住所、メールアドレス、電話番号、追跡コード、発送記録などを含めないでください。
