<h2 id="publications" style="margin: 2px 0 -15px;">Publications</h2>

<div class="publications">
<ol class="bibliography">

{% assign pubs = site.data.publications.main %}

{% for link in pubs %}

<li>
  <div class="pub-row" style="display:flex; flex-wrap:wrap; margin: 0 0 0.6rem 0;">
    <!-- Left column: thumbnail + badge -->
    <div class="col-sm-3 abbr" style="position:relative; padding-right:15px; padding-left:15px; min-width:160px; max-width:200px; flex: 1 1 180px;">
      {% if link.image %}
        <img 
          src="{{ link.image }}" 
          alt="{{ link.title | strip | escape }}" 
          class="teaser img-fluid z-depth-1" 
          loading="lazy"
          style="width:100%; height:auto; border-radius:6px;"
        >
      {% endif %}

      {% if link.conference_short %}
        <abbr class="badge" style="display:inline-block; margin-top:6px;">{{ link.conference_short }}</abbr>
      {% elsif link.journal %}
        <abbr class="badge" style="display:inline-block; margin-top:6px;">Journal</abbr>
      {% elsif link.type %}
        <abbr class="badge" style="display:inline-block; margin-top:6px;">{{ link.type }}</abbr>
      {% endif %}
    </div>

    <!-- Right column: title + meta -->
    <div class="col-sm-9" style="position:relative; padding-right:15px; padding-left:20px; flex: 1000 1 380px;">
      <!-- Title: link to PDF if available, else plain text -->
      <div class="title" style="font-weight:600; line-height:1.35;">
        {% if link.pdf %}
          <a href="{{ link.pdf }}" target="_blank" rel="noopener noreferrer">{{ link.title }}</a>
        {% else %}
          {{ link.title }}
        {% endif %}
      </div>

      <!-- Authors (HTML 허용: <strong>Sehoon Oh</strong> 강조 가능) -->
      <div class="author">{{ link.authors }}</div>

      <!-- Venue line (Journal vs Conference 분기) -->
      <div class="periodical">
        <em>
        {% if link.type and link.type == "Journal" or link.journal %}
          {%- assign jname = link.journal | default: link.conference -%}
          {%- if jname -%}{{ jname }}{%- endif -%}
          {%- if link.volume %}, {{ link.volume }}{%- endif -%}
          {%- if link.pages %}, {{ link.pages }}{%- endif -%}
          {%- if link.year %}, {{ link.year }}{%- endif -%}
        {% else %}
          {%- assign cname = link.conference | default: link.journal -%}
          {%- if cname -%}{{ cname }}{%- endif -%}
          {%- if link.year %}, {{ link.year }}{%- endif -%}
        {% endif %}
        </em>
      </div>

      <!-- Links -->
      <div class="links" style="margin-top:4px;">
        {% if link.pdf %}
          <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener noreferrer" style="font-size:12px;">PDF</a>
        {% endif %}
        {% if link.code %}
          <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener noreferrer" style="font-size:12px;">Code</a>
        {% endif %}
        {% if link.page %}
          <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener noreferrer" style="font-size:12px;">Project Page</a>
        {% endif %}
        {% if link.bibtex %}
          <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener noreferrer" style="font-size:12px;">BibTeX</a>
        {% endif %}
        {% if link.doi %}
          <a href="https://doi.org/{{ link.doi }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener noreferrer" style="font-size:12px;">DOI</a>
        {% endif %}
        {% if link.notes %}
          <strong><i style="color:#e74d3c">{{ link.notes }}</i></strong>
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
</div>
