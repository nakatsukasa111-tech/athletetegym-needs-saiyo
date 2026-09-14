# アスリートジムNeeDS ／ アスリートトレーナー採用LP

アスリートジムNeeDS（神戸市灘区六甲町4丁目1番15号）の、
アスリートトレーナー（スポーツトレーナー）募集用ランディングページ。

既存の[採用LP](https://github.com/nakatsukasa111-tech/saiyo-lp)とは**別ページとして並列**させます。

## コンセプト

> **選手の夢を、自分の成長に変えていく。**

軸は2本。そしてこの2本が循環していることが、このLPの背骨です。

```
①選手の夢・目標をサポートする  →  選手が結果を出す
              ↑                          ↓
   より高いレベルの選手を見る  ←  自分の技術が上がる ②
```

既存の採用LPが「10年続けられる働き方＝守り」を主軸にしているのに対し、
こちらは「上がっていく＝攻め」。同じ会社の2枚のLPが、別の動機の人を拾う関係です。

## 構成

| # | セクション | 内容 |
|---|---|---|
| 01 | HERO | キャッチ＋4つのピル＋CTA |
| 02 | NUMBERS | 10年+／9競技+／23-25万円／1-2名 |
| 03 | THE WORK | 業務内容6枚（測定・指導・野球ゴルフ・チーム・コンディショニング・研修） |
| 04 | WHO WE SUPPORT | 対象競技タグ／ジュニア・大人・プロ／チーム指導 |
| 05 | GROWTH | 代表の経歴・NeeDSメソッド・アドバイザー・学びの機会（**最厚セクション**） |
| 06 | WHO WE WANT | 探しています／向いていません |
| 07 | A DAY | 9:00〜21:00のシフト制 |
| 08 | WORK STYLE | 正社員／パートの待遇、手当 |
| 09 | COMPARE | 今の職場との比較 |
| 10 | STAFF VOICE | スタッフの声 |
| 11 | MESSAGE | 代表メッセージ |
| 12 | REQUIREMENTS | 募集要項 |
| 13 | FAQ | よくあるご質問 |
| 14 | ENTRY | 応募の流れ＋最終CTA |

## デザイン方針

**骨格と余白は女性向けLPの洗練さ、色と形と写真処理でアスリート感**という配分です。

| | 値 |
|---|---|
| ベース | `#0b0d0f` 〜 `#262b31`（黒〜スチールグレー） |
| 明面 | `#f3f4f5` / `#e7e9ec`（コンクリートグレー） |
| アクセント | `#e5722a`（既存LP・アスリートジムサイトのオレンジを継承） |
| ブランド青 | `#0d669b`（差し色としてのみ使用） |
| 英字見出し | Oswald（コンデンス体＝力強さ） |
| 和文見出し | Noto Sans JP 900 |
| 代表メッセージ | Noto Serif JP（明朝＝洗練の担保） |

- 「ゴツゴツ」感：角を落としたクリップパス／斜めのアクセントバー／斜めストライプ／モノクロ写真処理（ホバーでカラーに戻る）
- 「洗練」：セクション余白86px・細い罫線・eyebrow・行間1.95 ＝ women-v2 / women30 の型を継承
- 計測：GTM `GTM-P95C26ZR`（既存LPと同じコンテナ）
- `noindex,nofollow` を設定中。公開時に外すか判断してください

## 未対応（TODO）

画面上に赤い `TODO` バッジを出しています。**公開前に `.todo` を付けた要素をすべて削除してください。**

| 項目 | 内容 |
|---|---|
| CTAの遷移先 | 採用専用の公式LINEのURL。届き次第、全CTAと `utage/config.json` に設定 |
| ロゴ | 「Athlete NeeDS」のロゴ画像。現在はテキストのワードマークで代用（`.brand-mark` / `.ft-mark`） |
| 写真 | `images/` はすべて既存リポジトリからの仮置き。差し替え前提 |
| アドバイザー | 川岸良兼氏・上園啓史氏は掲載済。MLB／プロ野球トレーナー、メンタル・栄養の専門家のお名前 |
| 研修の頻度 | 週◯回／月◯回、1回あたりの時間 |
| シフト | 早番／遅番の具体的な時間割 |
| 帯同・遠征 | チーム指導時の移動・出張の有無（FAQ） |
| 福利厚生 | 社会保険・交通費・有給・健康診断などの記載可否 |
| スタッフの声 | アスリート部門のスタッフ2〜3名への取材 |
| UTAGE | `utage/config.json` の funnel_id / step_id / page_id |

## ファイル

| パス | 内容 |
|---|---|
| `index.html` | LP本体（CSS・JSともに内包した1ファイル構成） |
| `images/` | 画像（仮置き） |
| `utage/` | UTAGEへの自動反映スクリプトと設定 |
| `.github/workflows/deploy-utage.yml` | pushでUTAGEへ反映するワークフロー |

## UTAGEへの自動反映

`index.html` か `images/` を直してデフォルトブランチに push すると、
画像がUTAGEへ同期され、ページが更新されます（[needs-woman40-lp2](https://github.com/nakatsukasa111-tech/needs-woman40-lp2) と同じ仕組み）。

```
index.html ＋ images/          ← ここだけを直す（原本）
       │
       │ ① sync-images.mjs  新しい画像をUTAGEメディアへ自動アップロード
       │ ② build.mjs         画像URL・CTAを差し替えてHTMLを生成
       │ ③ deploy.mjs        UTAGE API へ PATCH
       ▼
   UTAGEのLP
```

### 設定（1回だけ）

1. UTAGE管理画面 → 右メニューの **API設定** でAPIキーを発行
2. GitHub → Settings → Secrets and variables → Actions → **New repository secret**
   - Name: `UTAGE_API_KEY`
3. UTAGE側でファネルとページを作成し、`utage/config.json` の
   `funnel_id` / `variants[].step_id` / `variants[].page_id` / `origin_cta` / `variants[].cta` を埋める

**設定が空のあいだ、ワークフローは何もせずスキップします**（設定前にジョブが赤くならないようにしています）。

## ローカル確認

```bash
python3 -m http.server 8000
# → http://localhost:8000
```
