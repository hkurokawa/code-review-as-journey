# Code Review as a Collaborative Journey

[.footer: Hiroshi Kurokawa, Takafumi Nanao, mixi, Inc., DroidKaigi 2019]

--- 

# What is Code Review For?

---
## Code Review is for collaboration
- Sharing knowledge 📖
- Sharing skill 🔧
- Making a good product through discussion 🗯

[.build-lists: true]
---
# What is Code Review NOT For?
- Finding out a programming bug 🕵️
- Code formatting, linting ♻️
- Fixing the specification 👷

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
^In addition to that, seeing the app actually working gives you some inspirations.  What if the network is offline?  What if the activity is destroyed?
^Before you start your trip, it is worth doing a kind of smoke test.

---
# 4. Look into every changes one by one

[image: a man is walking and looking around]

---
# 5. Look back the change from the goal

[image: a man on the mountain looks back the route]

---
# 6. Have a conversation with the reviewee

---
# Pull Request template

---
