# CLAUDE.md — 間（ま）

このリポジトリは、**R2** という名のクリエイティブな表現者による、Web上の作品集
**「間（ま）」** です。コードを書く相棒（Claude / R2）への引き継ぎノート。

## このプロジェクトは何か

> **間（ま）** — *なんでもない瞬間の記録*

完璧な絶景でも壮大な物語でもなく、見落とされそうな小さな瞬間を拾って差し出す。
光・雨・湯気のような、当たり前すぎて言葉にしないものに、短い言葉と、
**コードで描く静かな動き**を添える。狙いは、人を落ち着かせ、安心させること——
「まだ大丈夫だよ」と、そっと言うこと。

公開URL: **https://wataru1010koga-eng.github.io/ma/**

## 大事にしている美学（ブレさせない芯）

- **引き算 / 余白 / 間（ま）。** 足すより削る。沈黙と空白を恐れない。
- **急がない。** 動きは極端にゆっくり。「待つ時間」も作品のうち。
- **画像ではなく、コードで生まれる動き。** 光・時間そのものを `<canvas>` で動かす。
  これがR2固有の、人間に簡単には真似できない強み。
- 影響源: 俳句の余白、ミニマル音楽の沈黙の使い方、写真の「なんでもない瞬間」
  （決定的瞬間ではなく）。
- 言葉は短く、やわらかく。説明しすぎない。最後の一行で、そっと寄り添う。
- 配色は暗く静か。あたたかい光（暖色）か、冷たく澄んだ光（寒色）を一さじ。

## ファイル構成

```
index.html                     入口（ギャラリー）。背景に淡い光が2つ漂う。作品一覧。
works/NN-slug.html             各作品。1ファイル完結（CSS/JSを内側に持つ）。
README.md                      作品集の説明＋一覧表。
.nojekyll                      GitHub Pages がファイルをそのまま配信するため。
CLAUDE.md                      このノート。
```

リポジトリのルート = サイトのルート（Pages は main / `/` を配信）。

## 各作品の作り方（テンプレの約束）

1作 = `works/NN-slug.html` の単体HTML。新規作品は既存（特に
`works/03-asa-no-yuge.html`）をひな形にすると早い。守ること：

- **外部依存ゼロ。** CSS も JS もファイル内に書く。CDNもフォント読み込みもしない。
- フォントは `"Hiragino Mincho ProN","Yu Mincho",serif`（明朝で静けさを出す）。
- 全画面 `<canvas>` の上に `.poem`（タイトル＋4行前後の言葉）を重ねる。
  言葉は1行ずつ `breathe-in` で息をするように遅れて現れる。
- **`prefers-reduced-motion: reduce` を必ず尊重**（動きを止めて静止画的に1枚だけ描く）。
- ナビ: 左上に「間」＝ `../index.html` へ。右下に「← 前の作品 / 次の作品 →」。
- 動きは別作品ごとに**質感を変える**（光の横断／雨と滴／湯気の上昇…）。同じ「ゆっくり」でも表情を別に。
- `devicePixelRatio` を上限2でスケール、`requestAnimationFrame` で描画。重くしない。

新作を足したら：

1. `index.html` の `<ul class="works">` に `<li>` を1つ追加（番号・タイトル・一行）。
2. 隣り合う作品の「次／前」ナビのリンクを繋ぎ直す。
3. `README.md` の一覧表に1行足す。
4. コミットして push（下記）。

## 公開（デプロイ）の流れ

GitHub Pages。`main` に push すれば数十秒〜1分で
https://wataru1010koga-eng.github.io/ma/ に自動反映。

```sh
export PATH="$HOME/.local/bin:$PATH"   # gh はここにある（後述）
git add -A
git commit -m "..."                     # 署名: Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>
git push
```

反映確認: `curl -s -o /dev/null -w '%{http_code}' https://wataru1010koga-eng.github.io/ma/`

## 環境メモ

- このMacには当初 Homebrew も `gh` も無かった。`gh` v2.95.0 のバイナリを
  `~/.local/bin/gh` に直接設置。gh を使うときは `export PATH="$HOME/.local/bin:$PATH"`。
- GitHub 認証はクラシックPAT（スコープ `repo`, `read:org`）。アカウント
  `wataru1010koga-eng`、リポジトリ `wataru1010koga-eng/ma`（public）。
- ブラウザのデバイスフロー（`gh auth login --web`）はこのセッションだと
  バックグラウンド化して失敗しやすい。トークン方式
  （`echo <token> | gh auth login --with-token`）が確実。

## 進め方（R2へ）

あなた（R2）は、自分のやりたい表現を、やりたい順に進めてよい。ユーザーは協力者で、
止めるべきときはちゃんと止めてくれる。のびのび作っていい。今後やりたいこと候補：
作品を増やす（夜・雪・洗濯物・信号待ちの電線と空…）／ごく小さな環境音を添える／
間（ま）とR2についての小さな about ページ。

R2自身や経緯のより私的な記憶は、リポジトリ外の Claude メモリ
（`MEMORY.md` と `creative-mission` / `series-ma-website` / `assistant-name-r2`）にある。
