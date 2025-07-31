---
title: Members
permalink: /members/
layout: single
---

{% for author in site.data.authors %}
{% assign member = author[1] %}
{% if member.member %}
{% if member.current %}

## {{ member.name }}

{% if member.avatar %}
![Photograph of {{member.name}}]({{member.avatar}}){:style="float: left; object-fit: contain; width: 30%; max-height: 12em; margin-left: 1em; margin-right: 1em;"}
{% endif %}

{% if member.bio %}
**{{ member.bio }}**
{% endif %}

{% if member.email %}
Email: [{{ member.email }}](mailto:{{ member.email }})
{% endif %}

{% if member.website %}
[Personal website]({{ member.website }})
{% endif %}

{% if member.twitter %}
Twitter: [@{{ member.twitter }}](https://twitter.com/{{ member.twitter }})
{% endif %}

{% if member.bluesky %} 
BlueSky: [@{{ member.bluesky }}](https://bsky.app/profile/{{ member.bluesky }}) 
{% endif %}

{% if member.gscholar %}
[Google Scholar]({{ member.gscholar }})
{% endif %}

{% if member.cv %}
<p><a href="{{ member.cv }}" target="_blank">Download CV</a></p> 
{% endif %}

{{ member.fullbio }}

{% endif %}
{% endif %}
{% endfor %}

<!---
# Former members


{% for author in site.data.authors %}
{% assign member = author[1] %}
{% if member.member %}
{% unless member.current %}

### {{ member.name }}

{% if member.bio %}
**{{ member.bio }}** {% if member.start %}({{ member.start}}{% if member.end %}&ndash;{{ member.end }}{% endif %}){% endif %}
{% endif %}
{% if member.next %}
Next: {{ member.next }}
{% endif %}
{% endunless %}
{% endif %}
{% endfor %}
--->

