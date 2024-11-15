---
layout: talk
title: "Parsing with Prism in Sorbet"
url: null
slides: https://docs.google.com/presentation/d/1sw_V2_FfqTBfge46hBxLYxYcXKVy_LIp7CkqgphP9Ss/edit#slide=id.p
summary: |
  Sorbet is a gradual type checker for Ruby, and like many Ruby developer tools, it has its own parser. This means that every time a change is made to the Ruby language, teams at Stripe and Shopify need to implement those changes in Sorbet’s parser. This process is labor-intensive, slow, and prone to errors. There must be a better way!

  Enter, Prism. Prism is a new Ruby parser developed by Shopify. It is written in C and designed to be embedded in other Ruby tooling. In this talk, I’ll describe how I replaced the existing Sorbet parser with Prism, eliminating the toil of maintaining the Sorbet parser and taking one step toward uniting Ruby’s parsing ecosystem.
date: 2024-10-29
conference: WNB.rb Meetup
location: Virtual
---
