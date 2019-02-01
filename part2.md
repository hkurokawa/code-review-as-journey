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

tips to check

- Developer options
  - Show layout bounds
  - Change nimation scale

^ Unfortunately designers are not always familiar with Material Design or Android friendly UI.
So we need to check if it's on the Android way.

---

# UI behind UI

- Is handling errors?
- Is taking care of no data?
- Is using progress indicator properly?

tips to check

- add debug code directly
- `delay`
- Airplane mode

^ Only showing data is not everything.
We should handle various errors or empty state.

---
# Lifecycle

- Does it work on returning from home screen?
- Is supporting screen rotation?
- Does it work on killing process?
- Does it work on mashing buttons?

^ Imagine what you don't want users to do. Just do it.

---
# Performance

- Is working fast? 1s is slow.
- Can you scroll RecyclerView smoothly?
- TTI < 200ms

^ If you feel slow, you should measure the time to interactive.

---
# Build

- Warnings in build log or logcat
- Try proguard build or release build when relevant file was changed

^ changes related to build setting makes sometimes big issue.
Keep in mind to find troublesome problems as early as possible.

---
# Read code

- use Android Studio
- If you have question, don't hesitate to check actual operation.
- Is there any newly unnecessary code by that change.

^
codes which became unnecessary with changes are not easy to find.

---
# Values

We should share common values in our team.

- Easy to read
- Easy to change
- Proper package name

^
In our team, elegance of architecture doesn't matter.
Releases of Android platform or libraries whih we use are very frequent.
We need to update them as early as possible.
So we focus on how is it easy to change, fix or add new features.

---
# Layout

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
