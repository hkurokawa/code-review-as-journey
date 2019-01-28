# Code Review as a Collaborative Journey

[.footer: Hiroshi Kurokawa, Takafumi Nanao, mixi, Inc., DroidKaigi 2019]

--- 

# What is Code Review For?

---
## Code Review is for collaboration
- Sharing knowledge 📖
- Sharing skill 🔧
- Making a good product through discussion 🗯

^Hi, good morning everyone.
^I am Hiroshi Kurokawa and (Nanao-san says his name). Today I and Nanao-san are talking about code review.
^Is everyone doing code review?  Raise your hand if you are doing code review as a part of your daily job.
^Thank you.
^We are daily doing code review probably several times a day.  And, of course, our code is reviewed by peers as well.
^It is so common in the development process that we sometimes think we know well about code review.
^But I noticed some reviewers give considerate good feedback on my code and we could have fruitful dicussion about how to make our product better while I do not with other reviewers.
^I think there are some techniques about how to do a good code review.  And with regarding to Android app development, there are some tips and tricks to do efficient code review as well.
^So that is why I am here.

[.build-lists: true]
---
# What is Code Review NOT For?
- Finding out a programming bug 🕵️
- Code formatting, linting ♻️
- Fixing the specification 👷

^Before talking about code review.  I would like to give a brief definition about code review.  Especially about for what it is done.
^Code review has many aspects and when people think about code review, the image they have in their mind is sometimes rather different.
^Someone might think it is for finding out a bug while others might think it is for discussing specifications.
^To clarify what the code review is, I list up what the code review is not for.
^First, it is not for finding out a bug.
^Of course, sometimes a reviewer could find a potential bug and that is just good.
^But it is not the goal of code review.  It is mostly done through testing.
^Second, there are many formatting rules or lint warnings.  And it is also good to point out such things - it will anyway make the code better.
^But I think it is basically done by formatter or linter.
^Finally, 

[.build-lists: true]
---
# What information is required for Code Review?
- Goal
- Background
- Strategy
- Changes made
- Verification steps

[.build-lists: true]
---
# The story of code review

^OK.  Let's take a look at a typical code review process.  And, here, I am using an analogy for the code review process - a journey.
^Code review is like a journey.  You are handed over a map with a route on it, a Pull Request, and you walk down to the goal following the route and see how good the route is, I mean, verify how good the change is.

---
# 1. Understand the Background and the Goal

[image: a man is seeing a map]

^When you have a map, what do you do first?  Yes, find the goal and asking about the background.
^Where I am heading?  Why I have to get there?
^If you start walking without knowing where the goal is or why you do so, I am sure you cannot tell whether the route is good or bad.
^So remember to make sure what the goal is and the background before starting your journey.
^In the context of code review, it is same as reading the goal and the background of the Pull Request.
^If you have any questions about them, ask the reviewee.  The sooner, the better.

---
# 2. Go through the strategy and what was made

[image: a finger on the map]

^OK.  Now I can go for a trip!  Let's start!  No, no.  A well experienced traveller examines the route before starting his or her journey.
^Of course, you do not need to check the details.  But it is valuable to have a rough idea on how the route is.  Does the route avoid a mountain in clockwise or counter-clockwise?
^The route follows the shortest but hard path or longer but easy path?
^If the Pull Request you are reviewing describes some concerns, read them at this time.  You might be able to advise something here.
^For example, I once reviewed a Pull Request and noticed a standard widget can be used with a few modification instead of building a custom widget from scratch.
^So read through the strategy and the list of changes and any feedback if necessary.

---
# 3. Verify the change really takes you to the goal

[image: a man is driving on the road]

^Now you can start walking. And here is my advice.
^Drive a car to the goal instead of walking with your two legs.
^Just joking. But please note it is really easy to check whether the code *works* or not in the code review on the contrary to the real journey.
^I have many experiences that the code does not compile when Proguard is enabled, or the app crashes instantly due to timezone issue.
^So making sure the code at least runs or not is important before reviewing each changes in detail.
^In addition to that, seeing the actual running app gives you some inspirations.  What if the network is offline?  What if the activity is destroyed?
^Just like real test, it is worth doing smoke test on code review.

---
# 4. Look into every changes one by one

[image: a man is walking and looking around]

^Now is the time to look into changes in detail.
^I am not describing the techniques about how to review each changes.
^That part will be done later in this talk.
^One thing to note is that the rule of thumb is to think and feel as the reviewee does.
^As a proverb says, walk in his moccasins.
^You already know the background, the goal and the strategy of the journey.
^Then you are more likely to be able to understand why the change is made and why he or she takes this option not others.
^This is the very heart of the code review.  Thorough this process, you could share knowledge and skill with the reviewee efficiently.

---
# 5. Look back the change from the goal

[image: a man on the mountain looks back the route]

^Now you have done the code review.  Your job is done?
^Wait a moment.  Do not jump the gun.
^It is the time to look back your review.  Looking back your journey from the goal, then it might look different.
^In the begining of the code review, a change sometimes seem odd.  You do not get why the reviewee does that change.
^But putting it in the entire change, the change might make sense.
^So if you find one of your comments are off the point, take back it.

---
# 6. Have a conversation with the reviewee

^OK.  Now your review is done.
^Finally, give your feed back to the reviewee and have a conversation if necessary.
^After walking through the route with his or her mocassins, it is rather easy to have a communication with the reviewee.
^You know his or her pain, why, how and what he or she has made.  It helps you much to have an efficient conversation with the reviewee.

---
# Pull Request template

---
