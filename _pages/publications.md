---
permalink: /publications/
title: "Publications"
---

{% assign posts = site.posts %}

{% for article in posts %}
{% if article.publication %}
### {{article.title}}
{% assign length = article.authors | size %}
{% assign i = 2 %}
{% for author in article.authors %}{{author}}{%if i < length%}, {%elsif i == length%}{%if length > 2%},{%endif%} and {%else%}{%endif%}{%assign i = i | plus: 1%}{% endfor %}

{%if article.doi%}[*{{article.journal}}*](https://doi.org/{{article.doi}}){%else%}*{{article.journal}}*{%endif%}, {{article.year}} 

<!---
{% if article.pdbs %}
{% assign length = article.pdbs | size %}
PDB{%if length > 1%}s{%endif%}: {% for pdb in article.pdbs %} [{{pdb}}](https://doi.org/10.2210/pdb{{pdb}}/pdb){% endfor %}
{% endif %}
--->

<hr>
{% endif %}
{% endfor %}

\* = Authors contributed equally

# All articles and reviews

[Pubmed](https://pubmed.ncbi.nlm.nih.gov/?term=D%20Nathaniel%20Clarke%20or%20Donald%20N%20Clarke&sort=date)\
[Google Scholar](https://scholar.google.com/citations?user=xFyjzfoAAAAJ&hl=en)
