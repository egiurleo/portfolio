---
layout: page
paginate:
  collection: podcasts
title: Podcasts
---

<% paginator.resources.each do |podcast| %>

  <h3 style="margin-top: 1.25rem">
    <a href="<%= podcast.data.url %>"><%= podcast.data.podcast %> <%= podcast.data.episode %></a> <span style="font-weight: 4">: <%= podcast.data.title %></span>
  </h3>

  <p class="subtitle">
    <%= podcast.data.date.strftime("%B %Y") %>
  </p>

<% end %>

<%= render "pagination", metadata: site.metadata %>
