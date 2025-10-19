
<div class="publications">
  <!-- 按年份分组显示 -->
  {% assign grouped_publications = site.data.publications.main | group_by: "year" | sort: "name" | reverse %}
  
  {% for year_group in grouped_publications %}
  <h2 class="year">{{ year_group.name }}</h2>
  <ol class="bibliography">

    {% for link in year_group.items %}
    <li>
    <div class="col-sm-3 abbr">
      {% if link.conference_short %} 
      <abbr class="badge">{{ link.conference_short }}</abbr>
      {% endif %}
    </div>
    <div class="pub-row">
      <div class="col-sm-9 pub-content">
        <div class="title"><a href="{{ link.pdf }}">{{ link.title }}</a></div>
        <div class="author">{{ link.authors }}</div>
        <div class="periodical"><em>{{ link.conference }}</em></div>
        <div class="links">
          {% if link.pdf %} 
          <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>
          {% endif %}
          {% if link.code %} 
          <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>
          {% endif %}
          {% if link.page %} 
          <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Project Page</a>
          {% endif %}
          {% if link.others %} 
          {{ link.others }}
          {% endif %}
        </div>
      </div>
    </div>
    </li>
    <br>
    {% endfor %}
  </ol>
  {% endfor %}
</div>
