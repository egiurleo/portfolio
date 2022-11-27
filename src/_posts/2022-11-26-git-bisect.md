---
layout: post
title: "Automated debugging with git bisect and rspec"
summary: |
  Git bisect is a useful tool that can drastically speed up debugging if you know how to use it. In this blog post, I explain how to set up an automated git bisect for maximum productivity.
date: 2022-11-26
tags: git, productivity, ruby, rspec
---

<p class="post-date">
  <%= resource.data.date.strftime("%B %d, %Y") %>
</p>

<p class="note" markdown="1">
  ⚠️ **Note**: This article is cross-posted from my [old Dev.to blog](https://dev.to/emilysamp/how-to-run-an-automated-git-bisect-with-rspec-3dm3) and was originally written in 2021.
</p>

Debugging is hard. I mean like, really hard.

As a software engineer, I am constantly expanding my debugging tool belt in an effort to become a faster, more effective debugger. One tool that I've known about for a long time but only starting using recently is **git bisect**.

In this blog post, I'll explain what git bisect is, when it's useful, and how to use it to automate your debugging process with rspec.

## What is git bisect?

When you discover a bug in your code, you'll often start by asking yourself, "When was this bug introduced, and how?" This is easy enough if your project doesn't have very many commits -- you can go commit by commit and check when the bug was introduced. However, the older your project is, the harder this becomes. What if the bug was introduced 100 commits ago? You can't be expected to test every single one!

This is where `git bisect` comes in. Git bisect is a feature in [git](https://git-scm.com/) that helps you quickly find which of your commits introduced a bug using the power of [binary search](https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search).

(It's not necessary to understand how binary search works in order to use git bisect, but it's certainly interesting if you want to learn more about it!)

## How it works

First, you have to find an older commit that does not have the bug. This is called a "good" commit. Then, you find a more recent commit that does have the bug. This is a "bad" commit. You know that the bug was introduced sometime between these two commits, and git bisect will help you find out when.

Git bisect then performs a binary search, choosing commits in between the ones you specified and testing whether each one is "good" or "bad" (you can automate this step, or test each commit yourself).

After a few rounds of tests, git bisect will be able to identify which commit created the bug!

If this still sounds like a lot of work, I have good news -- you can provide git bisect with an rspec test so it can automatically determine whether a commit is good or bad. This makes the process almost entirely automatic, and while you go make yourself some coffee, git can let you know which of your commits created that bug you've been hunting.

## Scripted git bisect

Here are the steps you need to follow to run an automated git bisect with rspec:

### Step One: Start git bisect

You can tell git to start up a bisect with the following command:

```bash
git bisect start
```

This puts git into "bisect mode", which means you won't be able to do things like commit changes to your code. To exit bisect mode, run `git bisect reset` at any time.

### Step Two: Find a "good" commit

Look back in your commit history and find one that doesn't have the bug. Once you've found it, run the following command (replace `a09c728` with the SHA of your commit):

```bash
git bisect good a09c728
```

### Step Three: Find a "bad" commit

Find a more recent commit that does have the bug. Pass the commit SHA to the following command (replace `b6a0692` with your commit SHA):

```bash
git bisect bad b6a0692
```

### Step Four: Identify (or write) a failing rspec test

In order to automate the git bisect, you'll have to write a test that fails when the bug is present. You can tell `git bisect` to run this test on every commit, which will allow it to automatically determine if a commit is good or bad.

Here is an example rspec test in the file `spec/cat_spec.rb`:

```ruby
describe Cat do
  describe '#speak' do
    expect(Cat.new('Proxie').speak).to eq('Meow!')
  end
end
```

If this test fails, you'll know that the bug is present, and thus that a commit is "bad".

### Step Five: Run git bisect

Now you can run the automated git bisect with the following command:

```bash
git bisect run rspec spec/cat_spec.rb
```

Remember to replace `spec/cat_spec.rb` with the path to the test that you wrote in step four. Also remember that you can provide a line number to rspec (if you have many tests in the same file but only want to run one of them). For example, you could run:

```bash
git bisect run rspec spec/cat_spec.rb:2
```

### Step Six: Profit

Git bisect will test a variety of commits, and it will eventually find the first bad commit, aka the commit that introduced the bug!

The output will look something like this:

```bash
> 8b3c38f8680f653f07227f0cef42e54939de448b is the first bad commit
```

Now you can examine that commit and figure out exactly what part of your code introduced the bug!

### Step Seven: Clean up

Once you're done running git bisect, you can restore git to its normal state by running the following command:

```bash
git bisect reset
```

You can do this at any time during the bisect (even before you run it) to get out of "bisect mode" and get back to your normal workflows.

That's all there is to it! With a few commands and a good rspec test, you can simplify what would otherwise be a long and grueling debugging process. Git bisect has come in handy for me, and I hope it helps you out, too!
