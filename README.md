# M-StruX — Blogger テンプレート

M-StruX は、Blogger 向けに設計されたシンプル・軽量なカスタムテンプレートです。一般的な Blogger テーマとは異なり、テーマデザイナーや管理画面のレイアウト編集には対応していません。ガジェットの追加・削除・並び替えはレイアウト画面から行うことができず、カスタマイズはすべて XML（テンプレートHTML）を直接編集することで行います。そのため、ある程度 HTML / CSS / JavaScript の知識があるユーザー向けのテンプレートです。

表示まわりの機能は JavaScript によるクライアントサイドレンダリングで実装されておりjQueryもBootstrapも使っていません。アイコン用にFontAwesome 6のCSSを読んでいるだけで、あとはすべて自前のJavaScriptで動いています。

Bloggerの JSON Feed API を使って記事データを取得し、一覧・個別記事・ラベル・検索・アーカイブのページ切り替えをクライアントサイドで完結させるSPA構成にしました。

外部ライブラリに頼らないぶん、コードがシンプルで速い。カスタマイズするときも「どこを触れば何が変わるか」が追いやすいと思っています。

主な機能として、トップページの人気記事ヒーローバナーと注目記事の大型表示、ダークモード（OS連動＋手動切替）、記事内への目次自動生成、ラベルとハッシュタグの自動分類、SNSシェアモーダル、関連記事・前後記事ページャー、サイドバーの人気記事／新着記事タブ切り替え、ライトボックス、AdSense・Twitter・Instagram の遅延読み込みなどを備えています。レスポンシブ対応済みで、スマホではスライドイン式のハンバーガーメニューが表示されます。

また、メガメニュー、プロフィールカード、検索・アーカイブページの noindex 制御、構造化データ（JSON-LD）、Twitter Card、Canonical URL 自動設定など、SEO・UX を意識した機能も標準搭載しています。

---

![BloggerテンプレートM-StruX](https://i.imgur.com/k1ftUOu.jpeg "BloggerテンプレートM-StruX")

---

## 特徴

- **SPA（シングルページアプリケーション）構成** — JSON Feed API による動的描画
- **2カラムレイアウト** — メインコンテンツ左・サイドバー右（スマホは1カラム）
- **任意のページをフルページ** — サイドバーなしのページを表示
- **カード / リスト表示切替** — 記事一覧の表示形式を変更可能
- **人気記事ヒーローバナー** — トップページのみ上部に最大3件をグリッド表示
- **注目記事（Highlight Post）** — トップページ1件目に大きく表示
- **グローバルナビゲーション + プルダウンメニュー** — PC用ヘッダーナビ
- **メガメニュー対応** — 指定ラベルや最新記事をサムネイル付きで表示
- **ダークモード対応** — OSの設定に連動、手動切替ボタン付き
- **ページネーション** — 記事一覧・ラベル・検索・アーカイブページ対応
- **目次の自動生成** — `<div id="toc"></div>` を記事内に配置するだけ
- **人気記事 / 新着記事タブ** — サイドバーでタブ切り替え
- **関連記事** — 記事下部に同ラベルの記事を最大6件表示
- **前後記事ページャー** — 記事詳細ページに前の記事・次の記事リンク
- **著者プロフィールカード** — 記事末尾にSNS付きプロフィール表示
- **SNSシェアモーダル** — X(Twitter) / Facebook / はてなブックマーク / LINE / URLコピー
- **パンくずリスト** — 記事詳細ページに自動表示
- **ライトボックス** — 記事内の画像リンクをクリックで拡大表示
- **スケルトンスクリーン** — 読み込み中のちらつきを軽減
- **トップへ戻るボタン** — スクロール量に応じて自動表示
- **アーカイブドロップダウン** — サイドバーに月別アーカイブを選択式で表示
- **ラベル / ハッシュタグ分岐** — `#` から始まるラベルはハッシュタグとして別表示
- **レスポンシブ対応** — スマホはハンバーガーメニュー（スライドイン）
- **SEO対応** — OGP / Twitter Card / JSON-LD / Canonical / noindex
- **Gooleアドセンス対応** — アドセンスエリア
- **FontAwesome 6** 採用

---

## 使い方

### 1. テンプレートの適用

1. Blogger 管理画面 → **テーマ** → **HTMLを編集**
2. 既存のコードをすべて削除し、テンプレートの内容を貼り付けて保存

---

### 2. 必須設定

適用後、テンプレートHTML内の以下の箇所を編集してください。

### BLOG_CONFIG

```javascript
const BLOG_CONFIG = {
    blogId: "YOUR_BLOG_ID",
    viewMode: "card",          // "card" or "list"
    showLabels: true,
    showHashtags: true,
};
```

| 項目 | 内容 |
|---|---|
| `blogId` | Blogger のブログID |
| `viewMode` | 記事一覧表示形式（カード / リスト） |
| `showLabels` | スマホメニューにラベルを表示するか |
| `showHashtags` | スマホメニューにハッシュタグを表示するか |

ブログIDは Blogger 管理画面のURLに含まれる数字列です。

```text
https://www.blogger.com/blog/posts/【ここの数字】
```

> テーマ → HTMLを編集 → `BLOG_CONFIG` で検索

---

### SNS・プロフィール設定

```javascript
const SNS_CONFIG = {
    twitter:     "https://twitter.com/your_id",
    instagram:   "https://instagram.com/your_id",
    tiktok:      "https://tiktok.com/@your_id",
    youtube:     "https://youtube.com/@your_id",
    profile:     "https://www.blogger.com/profile/xxxxxxxx",
    cover:       "",
    description: "著者の自己紹介文をここに記入します。",
};
```

- `cover` を空欄にすると単色背景になります
- 記事下プロフィールカードにも反映されます

---

### OGP デフォルト画像

SNSシェア時のデフォルトサムネイルです。

```html
<meta content='https://example.com/your-default-image.jpg' property='og:image'/>
```

記事にサムネイルが存在しない場合、この画像が使用されます。

---

### ファビコン

必要に応じて `<head>` 内にファビコンタグを追加してください。

---

## ナビゲーションメニュー

### NAV_CONFIG による設定

ヘッダーナビゲーションは JavaScript 配列で構成されています。

```javascript
const NAV_CONFIG = [
    { label: "ホーム", url: "/" },

    {
        label: "カテゴリー",
        url: "#",
        children: [
            { label: "ニュース", url: "/search/label/News" },
            { label: "テクノロジー", url: "/search/label/Tech" },
        ]
    },

    {
        label: "Travel",
        url: "/search/label/Travel",
        mega: "label$Travel"
    },

    { label: "About", url: "/p/about.html" },
];
```

### mega プロパティ

| 値 | 内容 |
|---|---|
| `"label$ラベル名"` | 指定ラベルの最新4記事 |
| `"recent"` | 最新4記事 |
| `"random"` | ランダム4記事 |

---

### PCナビ（900px以上）

- フラットリンク
- ドロップダウンメニュー
- ホバーによるフェード表示
- メガメニュー対応

### スマホナビ（900px以下）

- ハンバーガーメニュー
- スライドイン表示
- 子要素アコーディオン展開
- ラベル / ハッシュタグ一覧表示
- 検索フォーム表示

---

## フィーチャードエリア（トップページのみ）

トップページ上部に注目記事を大型表示します。

- メインカード × 1
- サブカード × 2
- ドットオーバーレイ付きデザイン

Blogger の Highlight ウィジェットから記事を取得します。

※ レイアウト画面から 表示 / 非表示の選択が可能です

---

## 注目記事（Highlight Post）の設定

Blogger 管理画面の **「Highlight（注目記事）」ウィジェット** から設定します。

1. テーマ → レイアウト
2. 「Highlight（注目記事）」を編集
3. `postId` に記事IDを設定

または：

```javascript
useMostRecentPost: true
```

を指定すると最新記事を自動表示します。

※ レイアウト画面から 表示 / 非表示の選択が可能です

---

## 記事一覧表示

カードビュー / リストビューに対応しています。

```javascript
viewMode: "card"
```

または

```javascript
viewMode: "list"
```

スケルトンスクリーンによるローディング表示にも対応しています。

---

## 個別記事機能

### フルページ(サイドバーなし) / 通常ページ (サイドバーあり)切り替え

ハッシュタグに #FULL とついたページはサイドバーが非表示になり、フルページでの表示になります。

その際、ヘッダーの右端にサイドバーアイコンが表示され、クリックすると画面外右からスライドインします。

### 目次（TOC）

記事内の任意の位置に以下を記述してください。

```html
<div id="toc"></div>
```

`h2`・`h3`・`h4` 見出しを自動収集して目次を生成します。  
見出しが0件の場合は自動非表示になります。

サイドバーにハイライト対応の目次を表示できます。 true=表示 / false=非表示
```javascript
showSidebarTOC: true,    // サイドバー目次（記事ページのみ表示）
```

---

### ラベルとハッシュタグの使い分け

ラベル名の先頭に `#` を付けるとハッシュタグ扱いになります。

| ラベル名 | 扱い | 表示場所 |
|---|---|---|
| `ゲーム` | カテゴリ | 一覧・記事・サイドバー |
| `レビュー` | カテゴリ | 一覧・記事・サイドバー |
| `#RPG` | ハッシュタグ | 記事下部 |
| `#Nintendo` | ハッシュタグ | 記事下部 |

※ レイアウト画面から 表示 / 非表示の選択はできません

---

### コメント

Blogger 標準コメントフォームをアコーディオン形式で表示します。

---

### 関連記事

同一ラベルの記事を最大6件まで自動表示します。

---

### 前後記事ページャー

前の記事 / 次の記事リンクを自動生成します。

---

### ライトボックス

記事内画像をクリックするとモーダル表示されます。

---

## サイドバー機能

- プロフィールカード
- 人気記事 / 新着記事タブ
- ラベル一覧
- ハッシュタグ一覧
- アーカイブドロップダウン
- 検索フォーム
- ハイライト目次

---

## AdSense の遅延読み込み

記事内の任意の位置に以下を記述すると、スクロール時に広告が遅延読み込みされます。

```html
<div class="adsense-lazy" data-ad-slot="広告スロットID"></div>
```

テンプレート内の以下を変更してください。

```javascript
const client = "ca-pub-XXXXXXXXXXXXXXXX";
```

---

## Twitter（X）埋め込みの遅延読み込み

```html
<div class="twitter-lazy" data-tweet-id="ツイートID"></div>
```

画面付近に到達したタイミングで埋め込みを読み込みます。

---

## Instagram 埋め込みの遅延読み込み

```html
<div class="instagram-lazy" data-url="https://www.instagram.com/p/XXXXX/"></div>
```

Intersection Observer を利用して遅延読み込みされます。

---

## フッターのリンク編集

```html
<div class='footer-navigation'>
  <a href='/p/about.html'>ABOUT</a>
  <a href='/p/privacy-policy.html'>PRIVACY POLICY</a>
  <a href='/p/contact.html'>CONTACT</a>
  <a href='/p/sitemap.html'>SITEMAP</a>
</div>
```

固定ページURLに合わせて変更してください。

---

## SEO 対応

- Canonical URL 自動設定
- OGP メタタグ
- Twitter Card 自動切替
- JSON-LD（Article Schema）
- 検索 / アーカイブページ noindex

### Twitter Card

| 条件 | Card Type |
|---|---|
| サムネイルあり | `summary_large_image` |
| サムネイルなし | `summary` |

## Googleアドセンス 対応

メインコンテンツ上下 / 記事ページ本文上下 / サイドバー上下にアドセンスエリア

```javascript
const AD_CONFIG = {
    client: "ca-pub-XXXXXXXXXXXXXXXX", // ← パブリッシャーID
    slots: {
        "ad-main-top":      "スロットID", // メインカラム上
        "ad-main-bottom":   "スロットID", // メインカラム下
        "ad-post-top":      "スロットID", // 記事ページ本文上
        "ad-post-bottom":   "スロットID", // 記事ページ本文上
        "ad-sidebar-top":   "スロットID", // サイドバー上
        "ad-sidebar-bottom":"スロットID", // サイドバー下
    }
};
```

---

## CSS変数によるカラー設定

テンプレート冒頭の `:root` から変更できます。

| 変数 | 内容 | デフォルト |
|---|---|---|
| `--bg-color` | 背景色 | `#f8fafc` |
| `--text-main` | 本文色 | `#1e293b` |
| `--text-muted` | 補助色 | `#64748b` |
| `--accent` | アクセント色 | `#b45309` |
| `--accent-hover` | ホバー色 | `#e97834` |
| `--base-navy` | h2背景色 | `#1e3a5f` |
| `--sub-amber` | h3装飾色 | `#f59e0b` |
| `--header-bg` | ヘッダー背景 | `#1e3a5f` |
| `--sidebar-width` | サイドバー幅 | `300px` |
| `--max-width` | 最大横幅 | `1225px` |

---

## レスポンシブブレークポイント

| ブレークポイント | レイアウト変化 |
|---|---|
| 1024px 以下 | グリッド3列 → 2列 |
| 900px 以下 | スマホメニュー表示 / サイドバー非表示 |
| 768px 以下 | 関連記事4件目以降を非表示 |
| 600px 以下 | グリッド2列 → 1列 |

---

## 動作環境

- Blogger（Blogspot）
- Chrome 最新版
- Firefox 最新版
- Safari 最新版
- Edge 最新版

---

## 使用ライブラリ

- Font Awesome 6.4.2（CDN経由）

---

## 更新履歴

- 2026.05.01｜1.0.2｜関連記事周り調整 / ブログタイトルの見出し構造の修正
- 2026.05.08｜1.0.1｜サムネイル画像・記事内画像のWebP化を含む最適化
- 2026.05.01｜1.0.0｜正式版 配布開始

---

## ライセンス

個人利用のみ可。配布・販売は禁止です。
フッターの著作権表示の削除はしないでください。

© matsusan — https://blogger.matsusanjpn.com/

```
