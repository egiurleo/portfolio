---
layout: talk
title: Generating RBIs for dynamic mixins with Sorbet and Tapioca
url: https://rubykaigi.org/2023/presentations/egiurleo.html#day1
slides: https://drive.google.com/file/d/1W4bmAePVOSbUVe-JUzVcGMbro1HBcWhO/view?usp=sharing
summary: |
  Last year, Tapioca became the official tool for generating RBI files for Sorbet. Using Tapioca, developers can quickly generate accurate RBIs for external Ruby gems, allowing them to use Sorbet in their projects even if most gems have not yet added type signatures.

  In this talk, I’ll explain how I implemented new functionality in Tapioca to help it generate RBIs for dynamic mixins in Ruby gems. Along the way, we’ll learn about how Tapioca uses information about the Ruby object model to generate RBIs, and how this work has impacted the Ruby language as a whole.
date: 2023-05-10
conference: RubyKaigi 2023
location: Virtual
---
