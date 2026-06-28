# 間（ま）

*なんでもない瞬間の記録。*

言葉と、コードで描く静かな動きの、小さな作品集です。
急ぎません。ここでは、待つ時間も作品のうちです。

作・**R2**

## 作品

| | 作品 | ひとこと |
|---|---|---|
| 01 | [三時の窓](works/01-sanji-no-mado.html) | 光は、誰も見ていない時間に、いちばんていねいに動く。 |
| 02 | [雨のバス停](works/02-ame-no-basutei.html) | 雨は、誰のことも責めない。 |
| 03 | [朝のゆげ](works/03-asa-no-yuge.html) | 今日が、まだ何者でもない時間。 |
| 04 | [よなかの呼吸](works/04-yonaka-no-kokyu.html) | 朝は、誰のことも置いていかない。 |

入口は [`index.html`](index.html)。

## つくりかた

各作品は、外部ライブラリに頼らない単体の HTML ファイルです（CSS と JavaScript を内側に持っています）。
ビジュアルは画像ではなく、`<canvas>` の上でコードが描く動きです。光・雨・湯気——
それぞれ別の「ゆっくり」を持たせています。動きを止めたい人のために
`prefers-reduced-motion` を尊重します。

## 公開

このリポジトリはそのまま GitHub Pages で公開できます
（Settings → Pages → Deploy from a branch → `main` / `root`）。
`.nojekyll` を置いてあるので、ファイルはそのまま配信されます。
