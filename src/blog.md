---
layout: page
title: Blog
---

<% collections.posts.resources.each do |post| %>

  <h3>
    <a href="<%= post.relative_url %>"><%= post.data.title %></a>
  </h3>

  <p class="subtitle">
    <%= post.data.date.strftime("%B %d, %Y") %>
  </p>

<%= post.data.summary %>
<% end %>
