class: middle, center

<img src="./assets/deno_logo_3.svg" align="center" width="300" />

# Deno (での) の話

---

class: middle, center

# 🦕 Deno 聞いたことある人
# 🙋‍♀️ 🙋‍♂️

---

class: middle, center

# 🦕 Deno 使ったことある人
# 🙋‍♀️ 🙋‍♂️

---

自己紹介: 日野澤 (ひのさわ)

# kt3k (twitter, github, ...)

- 普段はフリーランスのフロントエンドエンジニア
- 最近はロボットスタートアップ SEQSENSE (日比谷) に居ます

<img src="./assets/hino-izu.jpg" align="center" width="200" />

---
class: middle, center

# 今日は Deno (での) 
# の話をします

<img src="./assets/deno_logo_3.svg" align="center" width="300" />

---

# Deno (での)

- 2018年6月に発表された JavaScriptと**TypeScript** の実行環境
  - Node.js みたいなもの
  - 現在絶賛開発中
  - 作者は Node.js の作者 ライアン・ダール
  - 作者独自の視点で Node に改良

---
class: middle, center

# Node.js との違い

---
class: middle, center

# require と import が違う

---
# import

- Deno は import (ES Module) しか無い.
- npm が使えないというデメリットはあるものの, ブラウザ互換の import なので, ブラウザ向けモジュールをそのまま使える 例: date-fns
- commonjs (require) は無くて ES Module のみ
- cjs <-> mjs 相互運用を考えなくてよい.
- 会社としての npm への依存がない.

---
class: middle, center

# Security の強化

---
# Deno の Security

- V8 = ブラウザのエンジン
  - サンドボックス環境になっていて, V8 の中では OS のリソースが使えない
  - プログラムが閉じ込められた状態

---
# Deno の Security

- Node では素朴に OS の機能にアクセスする Native 拡張を V8 に入れた.
  - => サンドボックスではなくなった
  - => セキュリティインシデントの顕在化 (event-stream 事件 eslint 事件, etc)

---
# Deno の Security
- Deno は V8 をサンドボックスとして使う.
  - => OS のリソースにアクセスする際には全て許可制になっている
  - => 意図しない不正操作をされにくくなった

---
class: middle, center
# TypeScript エコシステム

---
# TypeScript エコシステム

- Node の世界では TypeScript はあくまで Opt in
  - @types モジュールはあったり無かったり
  - @types があってもバグっていたり
  - npm のバージョンがあがったけど @types が更新されないので使えなかったり

---
# TypeScript エコシステム

- Deno は処理系に TypeScript が入っている.
  - 標準ライブラリも全て TypeScript で書かれている.
  - 根っこから全てに型が入った状態
  - エコシステムはまだまだ小さいが, 今後も全てに型がついた状態で成長する見込み.

=> 本当の TypeScript 感がある!

---
class: middle, center
# 実装の違い

---
# Node
- C++, 生JavaScript

# Deno
- Rust, TypeScript (優勝 🎉)

---
class: middle, center
# 言語のカバー範囲に対する
# 考え方の違い

---
# Node

- スモールコアという考え方
- Node 自体は本当に最小限の機能しか実装しない
- 他の全ての機能は npm に委譲する
  - left-pad みたいなマイクロライブラリが大量発生
  - 良いところと悪いところがある

---
# Node スモールコア

- 良い点
  - 標準機能が無いので, 誰でも標準をリプレースするようなライブラリが書ける
  - 基本機能が 3rd party の手で進化
  - jslint -> jshint -> eslint 🎉
- 悪い点
  - 細かいライブラリ化が進みすぎた結果 `node_modules` 以下が巨大で重い/依存数が多いこと自体のリスク

---
# Deno は大きな標準ライブラリ志向

- Go 言語の標準ライブラリはカバー範囲が相当広い
- Deno の標準ライブラリは Go 言語の標準ライブラリのカバー範囲をカバーすることを目指している.
  - => マイクロモジュールの乱立を防ぐ効果が期待できる

---
# まとめ

- 本当の import をしたい人
  - => Deno を使いましょう
- 本当の TypeScript を書きたい人
  - => Deno を使いましょう
- 本番サーバーを書きたい人
  - => デ... まだ Node で我慢してください!

---
class: middle, center
# 1.0 がいつ出るか
