# listing-images

Amazon の商品画像を **一時的に公開配信する**ためだけのリポジトリ。

## なぜ必要か
SP-API `patchListingsItem` は画像バイナリを受け取らず、**公開HTTPS URL を渡して Amazon に取得させる**方式のため。
Amazon は取り込み時に1回取得したあと自前CDN(`m.media-amazon.com`)で配信するので、
このリポジトリは「取り込みが終わるまで」生きていればよい。

## 置き場所のルール（重要）
- このフォルダは **事業ワークスペース(OneDrive/08_saitaichi_business)の外**に置くこと。
  git が事業ファイルへ物理的に到達できない状態を保つのが最大の防御。
- `.gitignore` は「全部無視 → 画像だけ許可」のホワイトリスト方式。
- `_source/` は加工前の生素材置き場。**コミットされない**。

## 入れてよいもの / いけないもの
- ✅ Amazon に載せる完成画像（純白背景・1600px以上推奨）
- ❌ 未公開商品のクリエイティブ（公開リポジトリなので誰でも見られる）
- ❌ 秘匿値を含むファイル全般（.env / トークン / 請求書 など）

## ファイル名の規約
`<asin小文字>_<スロット>_<版>_<日付>.jpg`
例: `b0hc753nzy_main_v1_20260809.jpg`

Amazon は URL をキャッシュするため、**差し替えるときは必ずファイル名を変える**こと。

## 公開URL
`https://raw.githubusercontent.com/SaceCaciy/listing-images/main/<パス>`
