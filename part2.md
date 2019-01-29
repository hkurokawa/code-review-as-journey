# Understanding background

Read the description

- Understand backgroud of the problem and check how it is solved

^ First of all let's check if the content is written as template.
If you don't know something, don't hesitate to ask reviewee it.
It's usual for people to forget anything to do.

---

# Operational check

Checkout the branch and build on your local.
`git worktree` command is very useful.

```
git worktree add ~/code-review/branch_name branch_name
android-studio.sh ~/code-review/branch_name
```

^ To avoid wasting your time, we usually do operational check before code review.
Sometime gradle builds fail after checking out the branch which has changes about databinding, build.gradle and so forth, 
using different directory makes build stable.

---

# UI

- Is along the guidelines of MD or your team?
- Is using animation properly?
- Is not like iOS UI?


Developer options are useful to check details.

^ Unfortunately designers are not always familiar with Material Design. 
So we need to check if it's on the android way.

---

# 裏のUI

- エラーをハンドリング適切にしているか
- データが0件の時でも不自然ではないか
- デバッグコードを仕込んで動かす
- 必要に応じて `delay` を入れてローディングが長くなるようにする
- エミュレータの通信速度の変更, air plane mode

^ APIやDBから取得した値を表示できただけで安心していないでしょうか?
必要なデータが取得できなかった場合、0件だった場合、すごく長い名前の表示なども確認するとQAでの手もどりが減らせます。

---
# ライフサイクル

- ホームボタンからの復帰
- 画面回転
- バックグラウンドプロセスキル
- 手当たり次第連打

^ 自分がされたら嫌だなと思う事を、思い付く限りやってみるのがお勧めです。
たぶんレビュイーはやってないでしょうから。

---
# パフォーマンス

- Activityの起動やRecyclerViewのスクロールなどスムーズか?
- TTI < 200ms

^ 一般的には画面遷移の際に、スクロールしたりボタンが押せるようになるまでの時間が300msくらいを越えると、ユーザーは遅いと感じると言われています。
遅いかも?と思ったら計測してみましょう。

---
# ビルド

- Logcat やビルド出力でWarningなどが増えてないか
- Proguardルールを変えたりライブラリを追加したらProguardビルドをする
- Debug, Releaseに関わるものはReleseビルドでもチェックする(firebase jsonなど)

^ ビルドに関する変更は些細なものであっても、面倒な問題を起こすことがあります。
リリース直前に気付くよりはコードレビューの時点で気付けると良いでしょう。

---
# コードを読む

- Android Studioで見る
- コードナビゲーションを利用
- 気になったら実際にコードを変えてみる
  - コードの削除により、不要になったコードなどはgithub diffだけでは気付かない
  
---
# 良いコード/悪いコード

大事にしたいルールやアーキテクチャーををチームで共有する

- わかりやすい
- 変更が簡単である
- 適切な名前空間

^ アーキテクチャーやデザインパターンについて、正しさや美しさばかりに傾倒するのは得策とは言えません。
あまり詳しくない人でも、簡単に機能追加や変更が可能になるように活用されるべきです。

---
# layout

- 気になるところは実際に変更を加えてみる
- 不要そうな属性やネストを消したときの挙動を確認する

---
# Githubの機能を活用する

- ignore whitespaces
- コードサジェスト機能
  
---
# フォーマット

- コーディングルールを設定で共有する
  - フォーマッタ
  - Lintの設定

```
# .gitignore
!.idea/codeStyles
!.idea/inspectionProfiles
```
^ コードスタイルやインスペクトルールはリポジトリに含める事ができます。
なるべく人間が気にしなくても良いように工夫しましょう。

---
# ライブラリの使い方

ソースを読む

- 不自然な記述や気になるところがあれば、他の実現方法が無いか調べる
- 知らないライブラリであれば、実際にソースを読んでみる

^ 別の手段が見つかるかもしれない

---
# リークしていないか

- Acitivityの強参照など
- 心配なコードを見つけたらプロファイラを見ながら動かしてみる

^ 画面を進んだり戻ったりしてみて、メモリの使用が増えていたら、リークしているかもしれない

---

# テストが適切に書かれいてるか

- メソッドの追加
- 条件文の追加などで、境界値が増えていないか

^ 後からテスト書くのは大変なので、簡単なものだけでも良いので、テストを書けるクラスには書いておいた方が得

---
# 変更していないところも見る

- 使われなくなったメソッドやフィールドの確認
- EventBusのように pubsub系に影響がないか
- minSdkVersionを上げた時などは多くの制御文を消せるかもしれない

---
# アプリの外側への影響

- パーミッションの変更
- Dangerousなものが追加されると自動アップデートが無効になる
- Application クラスをリネーム

---
# 全体を考えなおす

- 自分のコメントが勘違いだったりしないか考える。こういう事情があってこっちにした、という背景が見えてくることもある。
- 自分がイチから作るとしたらどうするか考える

^ single commnetよりはGitHubのコードレビュー機能便利

---
# フィードバックを行う

- 変更が必要であれば具体的な質問と依頼をする
  - コードスニペットを貼る
  - 不具合であれば、発生条件と手順
- 良いと思ったところは素直に褒める

^
気軽にコメントできる雰囲気を作る方がレビューが楽になる
気軽にPRを出せる and 気軽にレビューできる雰囲気

---

# [fit] FIN
