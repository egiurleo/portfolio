---
layout: page
paginate:
  collection: podcasts
title: Podcasts
---

<% paginator.resources.each do |podcast| %>

  <h3>
    <a href="<%= podcast.data.url %>"><%= podcast.data.podcast %> <%= podcast.data.episode %></a> <span style="font-weight: 4">: <%= podcast.data.title %></span>
  </h3>

  <p class="subtitle">
    <%= podcast.data.date.strftime("%B %Y") %>
  </p>

<%= podcast.data.summary %>
<% end %>

<%= render "pagination", metadata: site.metadata %>
