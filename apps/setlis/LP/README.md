# LP テンプレート

アプリ紹介LP用の流用可能デザインフォーマット。  
HTMLのテキスト・画像を差し替えるだけで新しいLPが完成します。

---

## ファイル構成

```
LP_format/
├── index.html           ← メインページ（日英同梱・これだけ編集すればOK）
├── style.css            ← 共通レイアウト・アニメーション（基本変更不要）
├── script.js            ← 言語切替・アニメーション制御（変更不要）
├── themes/              ← デザインテーマ（CSS変数のみ）
│   ├── midnight.css     … ダーク / 紺黒＋ブルー / テック・先進的
│   ├── obsidian.css     … ダーク / 黒＋オレンジ / 力強い・大胆
│   ├── snow.css         … ライト / 白＋ブルー / クリーン・信頼
│   ├── ivory.css        … ライト / ベージュ＋グリーン / 自然・ウェルネス
│   └── sakura.css       … ライト / ピンク＋ローズ / 柔らか・エレガント
├── images/              ← バッジ・ロゴ画像
│   ├── Download_on_the_App_Store_Badge_JP_RGB_blk_100317.svg（ライトテーマ用）
│   └── Download_on_the_App_Store_Badge_JP_RGB_wht_100317.svg（ダークテーマ用）
├── index_ja.html        ← 旧版（参照用・使用しません）
└── index_en.html        ← 旧版（参照用・使用しません）
```

---

## クイックスタート

### 1. テーマを選ぶ

`index.html` の `<head>` 内にあるテーマ読み込み行を変更：

```html
<!-- ↓ この○○○部分を変えるだけ！ -->
<link rel="stylesheet" href="themes/○○○.css" />
```

| テーマ名 | モード | 印象 |
|---------|-------|------|
| `midnight` | ダーク | テック・先進的 |
| `obsidian` | ダーク | 力強い・大胆 |
| `snow` | ライト | クリーン・信頼 |
| `ivory` | ライト | 自然・ウェルネス |
| `sakura` | ライト | 柔らか・エレガント |

> ⚠️ ライトテーマ使用時は App Store バッジも差替えてください  
> `wht_100317.svg`（白文字/ダーク用）→ `blk_100317.svg`（黒文字/ライト用）

### 2. テキスト・画像を差し替える

`index.html` を開いて、`▼` コメントで示されている箇所のテキスト・画像URLを変更するだけ。

主な編集ポイント：
- `<title>` — ブラウザタブ・SNSシェアタイトル
- `og:image` — SNSシェア時サムネイル
- ヒーローセクション — 背景画像・ロゴ・キャッチコピー
- 機能ダイジェスト — カード（絵文字・タイトル・説明）
- 機能詳細 — スクリーンショット・説明文
- CTA — App Store URL
- フッター — リンク・コピーライト

### 3. 言語テキストを書く

日英両対応のため、テキストは2つセットで書きます：

```html
<span data-lang="ja">日本語テキスト</span>
<span data-lang="en">English text</span>
```

ナビの言語ボタンで自動切替されます。

---

## カード・機能詳細の増減

### カードを増やす

`digest-grid` 内の `<div class="digest-card">〜</div>` をコピペ：

```html
<div class="digest-card" data-animate data-delay="6">
  <div class="digest-card-icon">🌟</div>
  <h3 class="digest-card-title">
    <span data-lang="ja">機能名</span>
    <span data-lang="en">Feature Name</span>
  </h3>
  <p class="digest-card-desc">
    <span data-lang="ja">説明文</span>
    <span data-lang="en">Description</span>
  </p>
</div>
```

### 機能詳細を増やす

`<div class="detail-item">〜</div>` をコピペ。  
奇数番目＝画像左、偶数番目＝画像右に自動配置。

---

## Google Play ボタンの追加（オプション）

`index.html` 内の Google Play コメントアウトを解除するだけ：

```html
<!-- この行を削除 → -->  <!--
<!-- ↓ このブロックが有効になります -->
<a href="https://play.google.com/store/apps/details?id=YOUR_APP_ID" ...>
  <img src="..." alt="Google Playで手に入れよう" class="store-badge-img" />
</a>
<!-- この行を削除 → -->  -->
```

---

## 技術仕様

- **レスポンシブ**: スマホ（〜480px） / タブレット（〜768px） / PC（1200px〜）
- **言語切替**: JavaScript + `data-lang` 属性 + localStorage保存
- **アニメーション**: IntersectionObserver + CSS transition
- **外部依存**: Google Fonts（Inter / Noto Sans JP）のみ
