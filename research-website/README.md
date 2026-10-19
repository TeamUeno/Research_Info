# 研究紹介サイト

2人の学生の研究を一般の方へ紹介する、HTML5・CSS3のみの静的サイトです。JavaScript、外部フォント、フレームワーク、ビルド作業は不要です。本文・氏名・所属・メールは仮情報です。研究成果や数値は掲載していません。

## ファイル構成

```text
research-website/
├── index.html          日本語トップ
├── research1.html      研究①の詳細
├── research2.html      研究②の詳細
├── contact.html        お問い合わせ
├── en/
│   └── index.html      英語トップ
├── css/
│   ├── style.css       共通デザイン・部品
│   └── responsive.css  タブレット・スマートフォン用
├── images/
│   └── .gitkeep        空ディレクトリ保持用
└── README.md
```

## 内容の編集

VSCodeのフォルダー内検索（Ctrl+Shift+F）で以下を検索・置換します。HTMLはUTF-8で保存してください。

| 内容 | 検索する文字 | 主な編集ファイル |
| --- | --- | --- |
| 共通テーマ | ここに共通研究テーマを入力 | index.html |
| テーマ説明 | ここに共通研究テーマの説明を入力してください | index.html |
| 研究タイトル | 研究タイトル① / 研究タイトル② | 日本語の各HTML（title、descriptionも確認） |
| 研究者名 | 研究者名① / 研究者名② | index.html、各研究詳細、contact.html |
| 研究概要 | ここに研究概要を入力してください | index.html、各研究詳細 |
| メール | researcher1@example.com / researcher2@example.com | index.html、contact.html、en/index.html |
| 所属 | 所属大学名（仮） / 研究室名（仮） | 日本語の各HTML |
| 英語の内容 | Enter the shared research theme here、Research title 01 / 02、Researcher name 01 / 02 | en/index.html |

メールは表示文字と `href="mailto:..."` の両方を更新します。英語版の説明文・所属も別途翻訳して更新してください。ヘッダー・フッターは各HTMLに直接記述しているため、共通情報は5ページとも確認します。言語切り替えは日本語・英語トップ間を移動します。研究詳細・お問い合わせの英語版は未作成です。

各研究詳細の `<section class="detail-section">` が編集単位です。セクションは自由に追加・削除できます。変更時は目次のリンクとセクションの `id` を一致させ、同じページ内でidを重複させないでください。見出しはページにh1を1つ、セクションにh2、下位項目にh3を使います。

## 研究画像の追加

画像を `images/` に保存し、該当する `.media-placeholder` を画像に置換します。図の場合は既存のfigureとfigcaptionを利用できます。

```html
<figure>
  <img src="images/research1-system.jpg"
       alt="研究システムの入力から出力までの処理の流れ"
       width="1200" height="800" loading="lazy">
  <figcaption>図1：研究システムの概要</figcaption>
</figure>
```

altは実際の図の内容に合わせて記述し、width・heightは実画像のサイズを指定します。英語版からは `../images/...` を使います。カード画像にも `.card-media` のプレースホルダーを置換して同様にimgを設置できます。メインビジュアルは `.hero-placeholder` を画像に置換するか、style.cssの `.hero` に背景を指定できます。背景だけで情報を伝えず、テーマの説明は本文にも残してください。

## デザインの変更

style.cssの `:root` に配色・最大幅・角丸をまとめています。共通部品はstyle.css、画面幅による調整はresponsive.cssを編集します。1050px以下でメニューを折り返し、700px以下でカードなどを1列にします。キーボードフォーカス・本文スキップリンク・動きの軽減設定に対応しています。

将来は詳細ページ内にfigure、動画、論文リンクなどを必要に応じて追加できます。動画は字幕と操作コントロール、グラフは本文での説明も用意してください。英語詳細ページを追加する際はナビゲーション、言語切り替え、lang、title、description、hreflangも更新します。

## VSCodeでの確認

1. この `research-website` フォルダーをVSCodeで開きます。
2. エクスプローラーからindex.htmlをブラウザーで開きます。ローカルファイルを開くだけで表示できます。
3. 自動更新を使う場合は任意でLive Server拡張を導入し、index.htmlを右クリックして「Open with Live Server」を選びます。拡張はサイト自体の依存関係ではありません。
4. 5ページのリンク、日英切り替え、Tabキーによる操作、メールリンクを確認します。
5. ブラウザーの開発者ツールで320px・375px・768px・1280px程度の幅を確認し、横スクロールや文字切れがないか確認します。

## GitHub Pagesでの公開

公開前に仮の氏名・メール・所属を実際の内容へ更新してください。

1. GitHubでリポジトリを作成します。
2. **このフォルダーの中身**（index.html、css、enなど）をリポジトリ直下へアップロードしてコミットします。
3. リポジトリのSettings → Pagesで、ブランチからの公開を選びます。
4. 対象ブランチ（例：main）と `/(root)` を選び、保存します。
5. 公開処理の完了後、Pagesに表示されたURLで確認します。

現在の親フォルダーごとリポジトリに登録する場合、サイトは公開URL末尾の `/research-website/` から閲覧できます。Pagesの公開元フォルダーに任意のサブフォルダーを直接指定する構成ではありません。すべて相対パスのため、リポジトリ名を含むURLでも利用できます。ファイル名の大文字・小文字は一致させてください。

## 確認状況

5ページの存在、相対リンクとアンカーの参照先、共通CSSの参照、日英のlang・hreflang、mailto、JavaScript不使用を静的に確認しています。レスポンシブ用CSSは実装済みですが、実ブラウザーでの画面幅別の描画確認およびGitHub Pagesへの実際の公開は未実施です。
