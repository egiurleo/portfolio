---
layout: post
title: "How to: code review with little or no context"
summary: |
  Reviewing code can be hard at the best of times, but sometimes, we have to review code with little or no context, whether that’s because we’re joining a new team, onboarding to a new project, or trying to learn about a new domain. How can you say whether or not code is safe to ship when you literally know nothing about it?

  In this blog post, I suggest an approach for reviewing PRs that can help you tackle your next PR review with confidence, even if you have little or no context on the code you’re reviewing.

date: 2025-01-15
tags: code-review
---

_Note: Thank you to [Alex Rocha](https://www.linkedin.com/in/alexcrocha/) for reviewing this post!_

Most software teams require code to be opened as a pull request (PR) and reviewed by another teammate before being merged and shipped. This means that, as software developers, we spend a good deal of time reviewing our teammates’ PRs. Often, we will have context on the code we’re reviewing, because we’ve been working alongside our teammates on the same projects. However, there are times when we have to review code with little or no context, whether that’s because we’re joining a new team, onboarding to a new project, or trying to learn about a new domain.

Reviewing code can be hard at the best of times, but under these circumstances, it can feel impossible. How can you say whether or not code is safe to ship when you literally know nothing about it? How can you spot bugs or inconsistencies in an unfamiliar domain?

Of course, the only real way to become an effective PR reviewer is to practice over time, but sometimes, you have to review a PR *now* to unblock your teammates. When you find yourself in that situation, what do you do?

In this blog post, I suggest an approach for reviewing PRs that can help you tackle your next PR review with confidence, even if you have little or no context on the code you’re reviewing.

## A template for PR reviews

In my opinion, the reason reviewing PRs without context is hard is because we don’t always review strategically. We glance at the PR description and scroll through the code, and our eyes glaze over looking at lines and lines of changes that don’t mean anything to us.

What if, instead of seeing a PR as lines of code, we see it as a story waiting to be read? What if we approach it with a template that can help us decode that story and make sense of something that might seem confusing at first?

When reviewing PRs, here are the four questions I ask myself. Once I have at least tried to answer all of them, I know I’ve reviewed the PR to the best of my ability.

### Question 1: Why does this PR exist?

This is the very first question I ask myself when looking at a PR. At the highest level, why is this change being made? Some potential answers are:
- It fixes a bug in the code
- It adds a new feature as part of a project
- It refactors existing code, enabling future changes
- It makes the application more accessible

Notice that the answers don’t have anything to do with *how* the code is changed. I would go so far as to say that you *shouldn’t* look at the code before trying to answer this question. If your teammates are writing clear PR descriptions (or bug tickets or whatever tool you use to store context like this), then this should be obvious.

### Question 2: How is the code changed?

Once you understand the *why* of the change, you can dig into the *how*. What changes are being made to the code to enable the goal stated in question one? Do you agree with the changes? Do you see any points of improvement?

An important thing to consider at this point is whether there is any proof that the code in the PR does what the author claims it does. Are there unit tests? Can you pull the code locally and look at any UI changes? If you don’t understand all the code in the PR, you can at least decide whether or not it achieves the stated goal by verifying these proofs.

### Question 3: What other approaches could the author have used? Why did they choose this one?

There are always multiple ways to approach any problem. Can you think of any other ways the author might have approached this PR? Is it clear why they chose their approach over the others?

(This question might be hard to answer, especially if the code is written in a language you’re not familiar with. That’s okay! Spend some time thinking about it anyway. Can you apply your knowledge of general software patterns to this unfamiliar code?)

### Question 4: What questions do I still have?

As you go through the three previous questions, note down anything that confuses you. Maybe you’re wondering why this change is necessary for the project. Maybe there are lines of code you don’t fully understand. Maybe you thought of another approach to the same problem and are wondering if the author had thought of it too. Gather up all these remaining questions and put them in your PR review!

## If you can’t answer the above questions

Even if you follow a systematic approach, you still might encounter a PR that is beyond your experience level, and that’s okay! Here are some more tips for when you’re really stuck.

### Go commit-by-commit

If your team has a culture of writing clean, descriptive commits, it might be helpful to review the PR one commit at a time, asking each of the four questions above as you go. Reviewing the code in smaller chunks can make the process more approachable.

### Ask your teammate(s)

Often, it just makes sense to review the PR with the author or another teammate. Go through the code together and ask them to help you answer the four questions above. Then, ask your teammate about their thought process – what information did they use to answer the questions? Can you learn from their approach?

### Ask an LLM

Sometimes, your teammates just aren’t available to help in cases like this. Maybe you’re working on a tight deadline, or you’re in a different timezone than the rest of your team. Whatever the case may be, an alternative approach is to get support from an LLM like ChatGPT or Claude. You can share the contents of the PR with the LLM and then ask your questions. Even if the results are not 100% accurate, it can at least help you get started.

(Note: if you are reviewing proprietary code, make sure you aren’t breaking any company or team rules before sharing code with an external tool.)

## Getting better over time

So far, this article has focused on a short-term approach. However, I think it is just as important to make long-term investments in your team culture and your own skills that will allow you to become a better PR reviewer in the future.

### Create a culture of clear PR descriptions and clean commits

Reviewing PRs is a lot easier to do when they have clear, thorough descriptions and small, clean commits. Some teams will already be excelling in this area, while others could probably use some work. If you notice that you and your teammates aren’t prioritizing these forms of asynchronous communication, do something about it! Speak to your manager or your teammates and see if you can shift the culture on your team.

### Read other people’s reviews

Do you have a teammate whose reviews are always so insightful? You can learn from them by making a point to read their reviews of your and your teammates’ PRs. What kinds of things do they focus on? What changes do they recommend? Those might be areas to focus on in your future PR reviews.

### Keep track of common review comments

As you read your teammates’ PR reviews, try to spot any patterns and write them down. (For example, maybe you notice that your teammate is good at identifying magic numbers or suggesting a specific refactoring pattern.) When it’s time for you to review a PR, refer back to your list and see if you can apply any of your learnings to your current review. Over time, you’ll be able to do this without your list.

### Timebox yourself

At first, reviewing PRs can take a long time. That is totally normal! However, it can be really stressful to feel like you’re not fulfilling other job functions, such as writing code. This is where timeboxing can come in handy. Talk to your manager about how long you should expect to spend on PR reviews every day. Then, sort your list of PRs to review by priority, set a timer, and review as much as you can in the allotted time.

While you might not get through your whole list of PRs, you will be able to practice the skill of reviewing while balancing the other work you need to do.

### Remember that it gets easier

Lastly, remember that reviewing PRs is a skill. Nobody starts out good at it. Even those of us who have been working as developers for years are required to re-up our review abilities as we start new jobs, learn new coding languages, or join new projects. Reviewing PRs might feel hard right now, but that just means you have lots of opportunity to improve. Good luck! I know you can do it.
