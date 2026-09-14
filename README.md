# 訪問看護ステーションかうむ ホームページ

## 公開先

**https://kaumu-calm.github.io/**

ログイン不要で、誰でも・どの端末からでも見られます。

### 内容を更新したいとき

1. このフォルダの中のファイルを直す
2. ターミナルで以下を実行（1〜2分でネットに反映されます）

```bash
cd ~/kaumu-hp
git add .
git commit -m "お知らせを更新"
git push
```

### 独自ドメイン（calm29.com）に変えたいとき

1. GitHubのリポジトリ設定 → Pages → Custom domain に `kaumu.calm29.com` などを入力
2. ドメインの管理画面で、CNAMEレコードを `nobimesi.github.io` に向ける
3. **`index.html` の中の `og:url` と `og:image` のURLも新しいドメインに書き換える**
   （LINEでURLを送ったときのサムネイル表示に使われているため）

## ファイルの中身

| ファイル | 中身 |
|---|---|
| `index.html` | ホームページ本体。5ページ分（ホーム／かうむについて／事業所概要／お知らせ／お問い合わせ）がこの1ファイルに入っています |
| `docs/juyo-jiko-setsumeisho.pdf` | 重要事項説明書（元のWordファイルから変換） |
| `docs/jigyo-unei-kitei.pdf` | 事業運営規程（元のWordファイルから変換） |
| `docs/kujo-taio-manual.pdf` | 苦情対応マニュアル（元のWordファイルから変換） |
| `images/hero-tree.jpg` | トップページの写真（Unsplash／商用利用可・クレジット表記不要） |
| `images/light-forest.jpg` | 予備の写真（現在は未使用） |

※ 元のWordファイル（`~/Downloads/` の3点）はそのまま残してあります。変更も削除もしていません。

## よくある更新のしかた

すべて `index.html` をテキストエディタで開いて書き換えます。

### 1. お知らせを追加・変更する

ファイルの下のほうにある `お知らせのデータ` という部分を探してください。

```javascript
var NEWS = [
  { date:"2026.09.14", tag:"お知らせ", title:"【見本】ホームページを公開しました。" },
  ...
];
```

この `{ ... }` を1行足せば、お知らせが1件増えます。新しいものを上に書いてください。
`date` が日付、`tag` が分類（お知らせ／ご案内 など自由）、`title` が本文です。

### 2. 写真を差し替える

`images/` フォルダに新しい写真を入れて、`index.html` の中の
`src="images/hero-tree.jpg"` を、新しいファイル名に書き換えます。

### 3. 色を変える

`index.html` の上のほう、`:root{` で始まる部分にすべての色がまとまっています。

| 名前 | 役割 |
|---|---|
| `--ground` | 背景の生成り色 |
| `--accent` / `--accent-deep` | 若草色（ボタン・見出しの色） |
| `--ink` | 文字色 |

※ `@media (prefers-color-scheme: dark)` と `:root[data-theme="dark"]` の部分は、
見る人の端末が「ダークモード」のときに使われる色です。同じように直してください。

## 独自ドメインへの引っ越し

このフォルダ（`index.html` + `docs` + `images`）をそのままレンタルサーバーに
アップロードすれば動きます。特別なプログラムやデータベースは使っていません。
