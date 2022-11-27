---
layout: page
paginate:
  collection: podcasts
title: Podcasts
---

<% paginator.resources.each do |podcast| %>

  <h3>
    <a href="<%= podcast.data.url %>"><%= podcast.data.podcast %></a> <%= podcast.data.episode %>: <%= podcast.data.title %>
  </h3>

  <p class="subtitle">
    <%= podcast.data.date.strftime("%B %Y") %>
  </p>

<% end %>

<%= render "pagination", metadata: site.metadata %>
