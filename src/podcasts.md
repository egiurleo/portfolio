---
layout: page
title: Podcasts
---

<% collections.podcasts.resources.each do |podcast| %>

  <h3>
    <a href="<%= podcast.data.url %>"><%= podcast.data.podcast %></a> <%= podcast.data.episode %>: <%= podcast.data.title %>
  </h3>

  <p class="subtitle">
    <%= podcast.data.date.strftime("%B %Y") %>
  </p>

<% end %>
