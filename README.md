# M-StruX — Blogger テンプレート

M-StruX は、Blogger 向けに設計されたシンプル・軽量なカスタムテンプレートです。一般的な Blogger テーマとは異なり、テーマデザイナーや管理画面のレイアウト編集には対応していません。ガジェットの追加・削除・並び替えはレイアウト画面から行うことができず、カスタマイズはすべて XML（テンプレートHTML）を直接編集することで行います。そのため、ある程度 HTML / CSS / JavaScript の知識があるユーザー向けのテンプレートです。

表示まわりの機能は JavaScript によるクライアントサイドレンダリングで実装されておりjQueryもBootstrapも使っていません。すべて自前のJavaScriptで動いています。

Bloggerの JSON Feed API を使って記事データを取得し、一覧・個別記事・ラベル・検索・アーカイブのページ切り替えをクライアントサイドで完結させる構成にしました。

外部ライブラリに頼らないぶん、コードがシンプルで速い。カスタマイズするときも「どこを触れば何が変わるか」が追いやすいと思っています。

---

![BloggerテンプレートM-StruX](https://i.imgur.com/SM193wl.jpeg "BloggerテンプレートM-StruX")

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
- **404ページ** — 専用404デザイン

---

## 利用規約

ご利用前に [利用規約](https://m-strux.matsusanjpn.com/p/terms-of-service.html) をご確認ください。
<br/>M-StruX のテンプレートをダウンロード、またはブログへ適用した時点で、 [利用規約](https://m-strux.matsusanjpn.com/p/terms-of-service.html) のすべての条項に同意したものとみなします。

利用規約に違反するブログが確認されております。<br/>
フッターのテンプレート制作者のコピーライトを削除・非表示・改変した場合、本テンプレートの利用許諾は自動的に失効します。その場合、利用者は本テンプレートの使用を継続する権利を失い、著作者は必要に応じて削除要請・利用停止申請・法的措置（DMCA申請を含む）を行うことがあります。

[利用規約違反通報フォーム](https://m-strux.matsusanjpn.com/p/forum.html)

※ 確認されている利用規約違反プロフィールならびにブログ<br/>
- ポリシー違反通報済み https://www.blogger.com/profile/10918075637547079444
- ポリシー違反通報済 削除済み https://000hot24h.blogspot.com/
- ポリシー違反通報済 削除済み https://docdao68.blogspot.com/

---

## ドキュメント

詳細なガイド、設定方法、解説は [公式ブログ](https://m-strux.matsusanjpn.com) をご覧ください。 

## 動作環境

- Blogger（Blogspot）
- Chrome 最新版
- Firefox 最新版
- Safari 最新版
- Edge 最新版

---

## 更新履歴

 [公式ブログ](https://m-strux.matsusanjpn.com/2026/05/blogger-about-mstrux.html) でご確認ください。 

- 2026.05.01｜1.0.0｜正式版 配布開始

---

## License Enforcement / Footer Copyright

個人利用のみ可。再配布・販売は禁止です。
フッターのテンプレート制作者のコピーライトは削除しないでください。

フッターのテンプレート制作者のコピーライトを削除・非表示・改変した場合、本テンプレートの利用許諾は自動的に失効します。その場合、利用者は本テンプレートの使用を継続する権利を失い、著作者は必要に応じて削除要請・利用停止申請・法的措置（DMCA申請を含む）を行うことがあります。
<br/>ご利用前に必ず [利用規約](https://m-strux.matsusanjpn.com/p/terms-of-service.html) をご確認ください。

© matsusan — [https://m-strux.matsusanjpn.com/](https://m-strux.matsusanjpn.com/)

The footer copyright notice of this template (“M-StruX designed by © matsusan”) must not be removed, hidden, or modified.

If the footer copyright is removed, hidden, or altered in any way, the license to use this template is automatically revoked.

Upon license revocation, the user loses the right to use this template, and the author reserves the right to request removal, issue takedown notices (including DMCA), and take any necessary actions to enforce copyright protection.

---

M-StruX [https://m-strux.matsusanjpn.com/](https://m-strux.matsusanjpn.com/)

## 支援

このテンプレートは完全無料で提供しております。もし活動を応援していただける場合は、更新や開発ツール利用のためのご支援を賜れますと幸いです。

[![Support via Coindrop](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhpkX8o_UdfTmYPmh04wDuIY3KeW1HwR23-siLCD-1ef1Rs96J0YLuaSwbNKe1c6FuWRx5GH7N2WBInxOHAue1qwd-b5ieuzpoQCHynZrwUuhV4LeMjpWkF7NagVtfEXXwNCy9f9OTitRoq1mFm_qwYqn3xXd11Oe-JVF3g15uEeXuV7t46KhyR1ZNd0bM/w200-h200/%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89.png)](https://coindrop.to/m-strux)
