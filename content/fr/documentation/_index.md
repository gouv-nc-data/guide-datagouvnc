+++
title = 'Documentation'
date = 2024-10-10T14:36:00+11:00
draft = false
+++
<h1>{{ .Title }}</h1>
<p>{{ .Description }}</p>

<ul>
  {{ range .Pages }}
    <li>
      <a href="{{ .RelPermalink }}">{{ .Title }}</a>
    </li>
  {{ end }}
</ul>
