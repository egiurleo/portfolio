---
layout: page
title: Talks
---

<% collections.talks.resources.each do |talk| %>

  <h3>
    <a href="<%= talk.data.url %>"><%= talk.data.title %></a>
  </h3>

  <p class="subtitle">
    <%= talk.data.conference %> • <%= talk.data.date.strftime("%B %Y") %> • <%= talk.data.location %>
  </p>

<%= talk.data.summary %>
<% end %>
