---
layout: page
paginate:
  collection: projects
title: Projects
---

<% paginator.resources.each do |project| %>

  <h3>
    <a href="<%= project.data.url %>"><%= project.data.title %></a>
  </h3>

  <p class="subtitle">
    <% if project.data.ongoing %>
      Ongoing
    <% else %>
      <%= project.data.date.strftime("%B %Y") %>
    <% end %>
  </p>

<%= project.data.summary %>
<% end %>

<%= render "pagination", metadata: site.metadata %>
