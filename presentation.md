# Code Review as a Collaborative Journey

[.footer: Hiroshi Kurokawa, Takafumi Nanao, mixi, Inc., DroidKaigi 2019]

^
Hi, good morning everyone.
I am Hiroshi Kurokawa and (Nanao-san says his name). Today I and Nanao-san are talking about code review.
Is everyone doing code review?  Raise your hand if you are doing code review as a part of your daily job.
Thank you.
We are daily doing code review probably several times a day.  And, of course, our code is reviewed by peers as well.
It is so common in the development process that we sometimes think we know well about code review.
But I noticed there are good reviews and not-good ones.
Some reviewers give considerate good feedback to a peer and they could have great dicussion to make the product better while others just point out some typos.
I think there are some techniques about how to do a good code review.  And with regarding to Android app development, there are some tips and tricks to do efficient code review as well.
Today we would like to share that.

--- 

# What is Code Review For?

^
Before talking about code review.  I would like to give a brief definition about code review.  Especially about for what it is done.
Code review has many aspects and when I just tell "code review", you would have different mental model than me.
Someone might think it is for finding out a bug while others might think it is for discussing specifications.

---
# What is Code Review NOT For?
- Finding out a programming bug 🕵️
- Code formatting, linting ♻️
- Discussing the specification 👷

^
To clarify what the code review is, I am listing up what the code review is NOT for so that you could get a clear image about code review.
First, it is not for finding out a bug.
Of course, sometimes a reviewer could find a potential bug and that is great.
But it is not the goal of code review.  It is mostly done through testing.
Second, there are many formatting rules or lint warnings.  And it is also good to point out such things - it will anyway make the code better.
But I think it is what formatter or linter is for.
Finally, the code review is not for discussing the specification of a product.
It is always useful to talk about the specification.  And even when the specification is fixed before a developer starts coding, everything might not work as planned.
In such cases, we have to have a discussion around the spcification and fix it.
Here what I just want to say is if you feel the spcification has a problem, involve the product manager and discuss it offline not on GitHub.

[.build-lists: true]
---
## Code Review is for collaboration
- Sharing knowledge 📖
- Sharing skill 🔧
- Making a good product through discussion 🗯

^
So, what code review is for?
In my opinion, it is for sharing knowledge, sharing skills and making a good product.  In short, it is for collaboration.
The first part of the process is to embrace how the reviewee thinks and solves a problem.
At first, you have no idea why the reviewee does this thing or that thing.
But through the code review, you will have a kind of heart-to-heart exchanges between the reviewee and finally get his or her idea.
And then you could give a feedback or a suggestion on how to improve their code.  This is the latter part of code review.
The reason why I use the word "journey" in the title of this talk is this process looks like a journey.
Not a physical one but rather a psychological one.
You walk down the way with the reviewee, have a conversation seeing scenary.
You will know what he or she thinks about it and why they choose this route not that route.
Sometimes you find out a better route or you might be told what you would overlook without the fellowship.
At last you and your reviewee get to the goal.
Until then, you could have a rather deep understanding on the problem you are solving and I am sure it would make your product better.
This is the purpose of code review.  Collaborating your coworker to make a good product.

[.build-lists: true]
---
# What information is required for Code Review?
- Goal
- Background
- Strategy
- Changes made
- Verification steps

^
To do this journey, you need some information.
First of all, the goal is most important.  What is the problem the Pull Request tries to solve?  For what we have to change our code?
And, next, there must be a background behind the change.  Sometimes its a disucssion in a hall or a chat on Slack.
Anyway, there is a context for this change and doing code review without knowing that background is like going through a tunnel without a light.
Next, if the Pull Request is rather large, take care about the strategy.  How your reviewee tackles the problem?
Just adding a patch to the existing code or trying to refactor a component to make the change easier?
Is he or she building up a custom view or adding a small modification on an existing one?
Keep in mind that what is the overall strategy of the change is.
And if you have any questions or concerns about it, ask the reviewee then.
The sooner the feedback is, the better for the reviewee to fix his or her change.
And, of course, you have a list of changes included in the Pull Request.
That might be just a sequence of commits or, if the reviewee is experienced, they might give you a list of brief description about what they have made.
Lastly, although not so many people add this information to their Pull Request, it would be great to know how to verify the change is correct.
I mean, how you can be sure that the change solves the problem and does not cause any bad side effects - regression bugs.

[.build-lists: true]

---
# Pull Request template

[image: a Pull Request template with dummy information]

^
Just for your help, here is a template I am using for Pull Request.
I am always asking people to fill out this template when submitting a Pull Request.
Then you can easily get the summary of the changes required for you to review.

---
# The story of code review

^
OK.  Let's take a look at a typical code review process.  And, here, I am using an analogy for the code review process - a journey.
Code review is like a journey.  You are handed over a map with a route on it, a Pull Request, and you walk down to the goal following the route and see how good the route is, I mean, verify how good the code is.

---
![](img/person-mountain.jpg)

[.footer: Photo by [Christopher Burns](https://unsplash.com/photos/-jbsw_GUK74?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 1. Understand the Background and the Goal

^
When you have a map, what do you do first?  Yes, find the goal.
And do not forget asking about the background as well as I told.
Why I have to get there?  What problem you want to solve?
If you start walking without knowing what the problem is, I am sure you cannot tell whether the route is good or bad.
If you have any questions about them, ask the reviewee.  The sooner, the better.

---
![](img/map.jpg)

[.footer: Photo by [Annie Spratt](https://unsplash.com/photos/qyAka7W5uMY?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 2. Go through the strategy and what was made

^
OK.  Now I can go for a trip!  Let's start!  No, no.  A well experienced traveller examines the route before starting his or her journey.
Of course, you do not need to check the details.  But it is valuable to have a rough idea on how the route is.  Does the route avoid a mountain in clockwise or counter-clockwise?
The route follows the shortest but hard path or longer but easy path?
If the Pull Request you are reviewing describes some concerns, read them at this time.  You might be able to advise something on them here.
For example, I once reviewed a Pull Request and noticed a standard widget can be used with a few modification instead of building a custom widget from scratch.
I gave that feedback on the reviewee and I and reviewee agreed on it would be rather better solution.  Although he had to remove most part of his code, we did not need to waste time on the custom widgets to be removed at last.
So read the strategy and the list of changes and give a feedback to the reviewee if necessary.

---
![](img/car-on-road.jpg)

[.footer: Photo by [delfi de la Rua](https://unsplash.com/photos/OrCvp6dFrKc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 3. Verify the change really takes you to the goal

^
Now you can start walking. And here is my advice.
Drive a car to the goal instead of walking with your two legs.
Just joking. But please note it is really easy to check whether the code *works* or not.
Just compile and run the app to see how it works.
This is why having the verification steps in the Pull Request is helpful.
I have many experiences that the code just does not compile when Proguard is enabled, or the app crashes instantly on a device I am using.
So make sure the code at least runs before reviewing each changes in detail.
In addition to that, seeing the actual running app gives you some inspirations.
What if the network is offline?  What if the activity is destroyed?
Review the change keeping these kind of points in your mind would make your review more thoughtful.

---
![](img/man-on-branch.jpg)

[.footer: Photo by [Caleb Jones](https://unsplash.com/photos/J3JMyXWQHXU?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 4. Look into every changes one by one

^
Now is the time to look into changes in detail.
I am not describing the techniques about how to review each changes.
That part will be done later in this talk.
One thing to note is that the rule of thumb is to think and feel as the reviewee does.
As a proverb says, walk in his moccasins.
You already know the background, the goal and the strategy of the journey.
This means you are more likely to be able to understand why each change is made and why he or she takes this option not others.
This is the very heart of the code review.  Thorough this process, you could share knowledge and skill with the reviewee efficiently.

---
![](img/sitting-on-cliff.jpg)

[.footer: Photo by [Vlad Bagacian](https://unsplash.com/photos/d1eaoAabeXs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 5. Look back the change from the goal

^
Now you have done the code review.  Your job is done?
Wait a moment.  Do not jump the gun.
It is the time to look back your review.  Looking back your journey from the goal, then it might look different.
In the begining of the code review, a change sometimes seem odd.  You do not get why the reviewee does that change.
But placing it in the entire journey, it might get another meaning.
So if you find one of your comments are off the point, do not hesitate to take back it.
And note if you find a change is awesome, just say that.
Review is not just pointing out a concern or a potential bug.
If you feel it is good, just express that.

---

![](img/journey-map.jpg)

[.footer: Photo by [rawpixel](https://unsplash.com/photos/lRssALOk1fU?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/journey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)]

# 6. Have a conversation with the reviewee

^
OK.  Now your review is done.
Finally, give your feed back to the reviewee and have a conversation on that.
After walking through the route with his or her mocassins, it is rather easy to have an efficient communication with the reviewee.
You know his or her pain, why, how and what he or she has made.  This is the collaboration.
The first part is done here.
I am switching to Nanao-san.
