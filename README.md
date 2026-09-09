# 送料チェッカー公開ページ

このフォルダーは、非公開のアプリ本体とは分離して公開する静的ページ一式です。公開先は、固定費0円でルート直下へ`app-ads.txt`も配置できるGitHubユーザーサイト`fumi231033.github.io`を予定しています。

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

## 公開時の手順

外部公開はユーザーから明示的な指示を受けてから行います。

1. 公開リポジトリ`fumi231033/fumi231033.github.io`を作成する
2. このフォルダーの内容をリポジトリのルートへ配置する
3. GitHub Issuesを有効にする
4. GitHub Pagesを`main`ブランチのルートから公開する
5. ログアウト状態でトップ、プライバシーポリシー、問い合わせページ、Issueフォームを確認する
6. `app/`で`npm run check:public-web-endpoints`を実行する

## `app-ads.txt`について

初回公開版では広告SDKを使用しないため、`app-ads.txt`はまだ置きません。将来AdMobを導入する場合に、AdMobから取得した正式な1行を改変せず、このフォルダーのルートへ`app-ads.txt`として追加します。Publisher IDや広告ユニットIDの推測値・仮値は公開しません。

公開ページ、Issue、コミットへ、利用者の氏名、住所、メールアドレス、電話番号、追跡コード、発送記録などを含めないでください。
