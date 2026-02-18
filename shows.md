---
layout: default
title: shows
---

# shows

tell them you're here to see Xmachina!


<!-- ## upcoming

<ul id="shows-upcoming">
{% for show in site.data.shows %}
  <li class="show" data-date="{{ show.date | date_to_xmlschema }}">
      {{ show.date | date: '%a, %b %d, %Y'  }} @ {{ show.venue }} // {{ show.tix }}
  </li>
{% endfor %}
</ul>

## past
<ul id="shows-past"></ul>


<script>
(function () {
  const now = new Date();
  const pastList = document.getElementById("shows-past");

  document.querySelectorAll("#shows-upcoming .show").forEach(li => {
    const d = new Date(li.dataset.date);
    if (!isNaN(d) && d < now) {
      li.classList.add("is-past");
      pastList.prepend(li); // moves node
    }
  });
})();
</script> -->

<div class="shows-wrap">

  <h2>upcoming</h2>

  <table id="shows-upcoming" class="shows">
    <thead>
      <tr>
        <th>Date</th>
        <th>Venue</th>
        <th>Link</th>
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
        <th>Date</th>
        <th>Venue</th>
        <th>Link</th>
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
