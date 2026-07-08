---
layout: page
permalink: /publications/
title: Publications
description:
nav: true
nav_order: 1
topics:
  - slug: culture-alignment
    name: Culture &amp; Alignment
  - slug: agents
    name: Agents
  - slug: interpretability
    name: Interpretability
  - slug: safety
    name: AI Safety &amp; Robustness
  - slug: multilinguality
    name: Multilinguality &amp; Translation
---
<!-- _pages/publications.md -->
<div class="publications">

An up-to-date list is available on <a href="https://scholar.google.com/citations?hl=en&user=vT4f678AAAAJ">Google Scholar</a>. * denotes equal contribution.

<div class="topic-filter" role="tablist">
  <span class="topic-filter-label">TOPIC:</span>
  <button type="button" class="topic-pill active" data-topic="all">All</button>
  {%- for topic in page.topics %}
  <button type="button" class="topic-pill" data-topic="{{ topic.slug }}">{{ topic.name }}</button>
  {%- endfor %}
</div>

{% bibliography -f {{ site.scholar.bibliography }} %}

</div>

<script>
  (function () {
    var pills = Array.prototype.slice.call(document.querySelectorAll('.topic-filter .topic-pill'));
    var rows = Array.prototype.slice.call(document.querySelectorAll('.publications ol.bibliography .row[data-topic]'));

    function applyFilter(topic) {
      // "All" shows every paper (including ones without a topic pill, e.g. older
      // one-off work); a specific pill shows only papers tagged with that topic.
      rows.forEach(function (row) {
        var show = topic === 'all' || row.getAttribute('data-topic') === topic;
        var li = row.closest('li');
        if (li) { li.classList.toggle('hidden-card', !show); }
      });
      pills.forEach(function (p) {
        p.classList.toggle('active', p.getAttribute('data-topic') === topic);
      });
    }

    pills.forEach(function (pill) {
      pill.addEventListener('click', function () {
        applyFilter(pill.getAttribute('data-topic'));
      });
    });
  })();
</script>
