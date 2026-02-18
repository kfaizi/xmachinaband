---
layout: default
title: shows
---

# shows

tell them you're here to see Xmachina!

<div class="shows-wrap">

  <h2>upcoming</h2>

  <table id="shows-upcoming" class="shows">
    <thead>
      <tr>
        <th>when</th>
        <th>where</th>
        <th>info</th>
      </tr>
    </thead>
    <tbody>
    {% for show in site.data.shows %}
      <tr class="show" data-date="{{ show.date | date_to_xmlschema }}">
        <td>{{ show.date | date: "%a, %b %d, %Y" }}</td>
        <td>{{ show.venue }}</td>
        <td>{{ show.tix }}</td>
      </tr>
    {% endfor %}
    </tbody>
  </table>

  <h2>past</h2>

  <table id="shows-past" class="shows">
    <thead>
      <tr>
        <th>when</th>
        <th>where</th>
        <th>info</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>

</div>


<script>
document.addEventListener("DOMContentLoaded", () => {
  const upcomingBody = document.querySelector("#shows-upcoming tbody");
  const pastBody = document.querySelector("#shows-past tbody");
  if (!upcomingBody || !pastBody) return;

  const now = new Date();

  upcomingBody.querySelectorAll(".show").forEach(row => {
    const d = new Date(row.dataset.date);
    if (!isNaN(d) && d < now) {
      row.classList.add("is-past");
      pastBody.appendChild(row);   // keeps reverse order
    }
  });
});
</script>
