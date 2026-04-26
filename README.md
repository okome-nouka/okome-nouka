# お米農家 HP — デプロイ・運用ガイド

鹿児島県産ひのひかり・さつまゆきもちのシンプルな農家直売HPです。  
Netlify の無料プランで運用できます。

---

## ファイル構成

```
okome-nouka/
├── index.html   # メインページ（全セクション）
├── style.css    # スタイルシート
└── README.md    # このファイル
```

---

## Netlify へのデプロイ手順

### 方法A: ドラッグ＆ドロップ（最も簡単）

1. [https://app.netlify.com/drop](https://app.netlify.com/drop) をブラウザで開く
2. **`okome-nouka` フォルダ**をそのままページにドラッグ＆ドロップ
3. 自動でデプロイが始まり、`https://xxxxxxxx.netlify.app` のURLが発行される
4. 「Site settings」→「Change site name」からURLを好きな名前に変更可能

> **注意:** フォルダごとドラッグ（中のファイルではなく `okome-nouka/` フォルダ自体）

---

### 方法B: GitHub連携（更新が楽になる）

1. GitHubに `okome-nouka` リポジトリを作成し、3ファイルをプッシュ
2. Netlify > "Add new site" > "Import an existing project" > GitHub連携
3. Build設定は空欄のまま（ビルド不要）で「Deploy site」

---

## Netlify Forms セットアップ（必須）

フォームはすでに `data-netlify="true"` が設定済みです。  
**デプロイ後に以下の操作が必要です。**

### フォームの確認

1. Netlify管理画面 > 該当サイト > **「Forms」タブ**を開く
2. `contact` という名前のフォームが表示されていることを確認
3. 表示されていない場合はサイトを再デプロイしてください

---

## フォーム送信通知メール設定

送信時に **dwe.sew.mac@gmail.com** へメール通知を届ける手順。

### 手順

1. Netlify管理画面 > 該当サイト > **「Forms」タブ**
2. フォーム一覧から「**contact**」をクリック
3. 右上の「**Form notifications**」ボタンをクリック
4. **「Add notification」**→「**Email notification**」を選択
5. 以下を入力して「Save」

   | 項目 | 入力値 |
   |------|--------|
   | Email to notify | `dwe.sew.mac@gmail.com` |
   | Custom email subject | `【お米農家】お問い合わせが届きました` |

6. 保存後、テスト送信してGmailに届くか確認する

> **Gmailのフィルタ注意:** 届かない場合は迷惑メールフォルダを確認してください。  
> 送信元は `forms@netlify.com` になります。

---

## カスタムドメイン設定（任意）

独自ドメインを使いたい場合：

1. ドメインを取得（お名前.com、ムームードメインなど）
2. Netlify > Site settings > **「Domain management」** > 「Add custom domain」
3. DNSをNetlifyのネームサーバーに変更するか、DNSレコードを設定
4. SSL証明書は Netlify が自動発行（Let's Encrypt）

---

## 実際の写真への差し替え

現在は背景色のプレースホルダーを使用しています。  
写真ができたら以下の方法で差し替えます。

### ヒーローセクション

`style.css` の `.hero-image-placeholder` を編集：

```css
/* style.css の .hero-image-placeholder に追記 */
.hero-image-placeholder {
  background-image: url('images/hero.jpg');
  background-size: cover;
  background-position: center;
}
```

### 商品画像

`style.css` の各商品クラスに追記：

```css
.product-image--hinohikari {
  background-image: url('images/hinohikari.jpg');
  background-size: cover;
  background-position: center;
}

.product-image--yukimochi {
  background-image: url('images/yukimochi.jpg');
  background-size: cover;
  background-position: center;
}
```

画像ファイルは `okome-nouka/images/` フォルダを作って保存してください。

---

## 更新方法（テキスト変更など）

`index.html` をテキストエディタで開いて直接編集します。  
更新後は Netlify に再デプロイしてください。

- ドラッグ＆ドロップ方式：再度フォルダをドロップするだけ（最新版で上書き）
- GitHub連携方式：プッシュすると自動デプロイ

---

## サポート

- Netlifyヘルプ: [https://docs.netlify.com](https://docs.netlify.com)
- Netlify Forms: [https://docs.netlify.com/forms/setup/](https://docs.netlify.com/forms/setup/)
