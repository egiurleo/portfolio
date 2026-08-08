---
layout: page
paginate:
  collection: talks
title: Talks
---

<% paginator.resources.each do |talk| %>

  <h3>
    <% if talk.data.url && !talk.data.url.empty? %>
      <a href="<%= talk.data.url %>"><%= talk.data.title %></a>
    <% else %>
      <%= talk.data.title %>
    <% end %>
  </h3>

  <p class="subtitle">
    <%= talk.data.conference %> • <%= talk.data.date.strftime("%B %Y") %> • <%= talk.data.location %> •
    <a href="<%= talk.data.slides %>">
      &#8599; slides
    </a>
  </p>

<%= talk.data.summary %>
<% end %>

<%= render "pagination", metadata: site.metadata %>
