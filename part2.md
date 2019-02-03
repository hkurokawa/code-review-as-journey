# Understanding the background

Read the description

- Understand the background of the problem and check how it is solved

^ So I'm gonna dig a little deeper into each steps.
First of all let's check if the content was written using the template.
If there is something you don't understand, don't hesitate to ask reviewee it.
It's usual for people to forget writing some details.

---

# Operational check

Checkout the branch and build it locally.
The `git worktree` command is very useful.

```
git worktree add ~/code-review/branch_name branch_name
android-studio.sh ~/code-review/branch_name
```

^ To avoid wasting our time, we usually do operational check before code review.
Sometimes gradle builds fail after checking out a branch which has changes about databinding, build.gradle and so forth,
using a different directory helps make the build stable.

---

# UI

- Is it along the guidelines of Material Design or your team's?
- Is it using animation properly?
- Is it not like iOS UI?

tips to check

- Developer options
  - Show layout bounds
  - Change animation scale

^ Unfortunately designers are not always familiar with Material Design or Android friendly UI.
So we need to check if it's done the Android way.

---

# UI behind UI

- Is it handling errors?
- Does it work even with no data?
- Is it using the progress indicator properly?

tips to check

- add debug code directly
- use `delay`
- Airplane mode

^ Only showing data is not everything.
We should handle various errors or empty state.

---
# Lifecycle

- Does it work after returning from the home screen?
- Does it support screen rotation?
- Does it work after the process was killed?
- Can it handle buttons being tapped very fast?

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
Releases of Android platform or libraries which we use are very frequent.
We need to update them as early as possible.
So we focus on how is it easy to change, fix or add new features.

---
# Layout

- unnecessary stuffs
- unnecessary nest

^
If you have any concern, change code and check how it works.

---
# code format

- share your coding rules
  - formatting
  - rules of lint

```
# .gitignore
!.idea/codeStyles
!.idea/inspectionProfiles
```

^
Settings aboutg coding style or code inspection can be shared in repository.
Save your time with automation.

---
# 3rd party libraries

- Is trusty?
- Is maintained well?
- Is there better alternatives?

^
If you don't know the new library,
read the document and source code.
Then you may find better methods or classes.

---
# leaks

- Strong reference to Acitivity
- Use it watching the profiler of AS

^
When you repeat screen transition,
memory usage may increase.
that's the leak

---

# Tests

- Are proper tests added?
- Are tests enough for additional conditions or boundary values?

^
since it's often hard to add tests later,
we had better write tests as ealy as possible.

---
# Side effects

- Adding Permission
- Moving Application class

^
If you add new Dangerous permission to the AndroidManifest,
auto update will be disabled.
So check if it's really necessary permission.

And another one is an actual failure which I made.
When I changed package name of Application class as a part of refactoring,
do you know what happened?
Users couldn't launch app from shortcut on their home screen,
because the entity of shortcut is like a bookmark which refers to the intent of former package name of application.

---
# Look back

- Check if your opinion or recognition is right.
- Imagine what you would  do if you were the reviewee.

^
In the end of code reading, you may have different impression from the begining.
To avoid submit misunderstanding comment,

---
# Give your feedback

- Feedback details to improve the code
  - Use code suggestion
  - Conditions and steps to repro bug
- Praises are welcome

^
If you think some changes is necessary, feedback your suggestion as detail as possible.

And if you feel good to see the code, don't hesitate to feedback your feeling.
That helps you to be positive to communicate each other.

---

# [fit] FIN
