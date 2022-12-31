---
authors: {{authors}}
title: {{title}}  
year: {{date | format("YYYY")}}   
citekey: @{{citekey}}  
---

## Tags
{% for t in tags %}#{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}

## Research note

{% persist "notes" %}
{% endpersist %}

## Annotations
{% persist "annotations" %}

{% set annotations_yellow = annotations | filterby("color", "contains", "#ffd400") -%}
{% set annotations_yellow = annotations_yellow | filterby("date", "dateafter", lastImportDate) -%}

{% set annotations_green = annotations | filterby("color", "contains", "#5fb236") -%}
{% set annotations_green = annotations_green | filterby("date", "dateafter", lastImportDate) -%}

{% set annotations_red = annotations | filterby("color", "contains", "#ff6666") -%}
{% set annotations_red = annotations_red | filterby("date", "dateafter", lastImportDate) -%}

{% set annotations_blue = annotations | filterby("color", "contains", "#2ea8e5") -%}
{% set annotations_blue = annotations_blue | filterby("date", "dateafter", lastImportDate) -%}

{% set annotations_purple = annotations | filterby("color", "contains", "#a28ae5") -%}
{% set annotations_purple = annotations_purple | filterby("date", "dateafter", lastImportDate) -%}

{% set annotations_comment = annotations | filterby("date", "dateafter", lastImportDate) -%}


{% if (annotations_green.length > 0) or (annotations_yellow.length > 0) or (annotations_red.length > 0) or (annotations_blue.length > 0) or (annotations_purple.length > 0) or (annotations_comment.length > 0)%}

#### Imported: {{importDate | format("YYYY-MM-DD h:mm a")}}

{% if annotations_yellow.length > 0 %}
{%- for annotation in annotations_yellow %}
{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]] 
{% endif %}
{% if annotation.annotatedText %}
> [!contribution]+ Contributions<br>
> - [ ] Completed
> {{annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}

{% if annotations_blue.length > 0 %}
{%- for annotation in annotations_blue %}
{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]] 
{% endif %}
{% if annotation.annotatedText %}
> [!result]+ Results<br>
> - [ ] Completed
> {{annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}

{% if annotations_purple.length > 0 %}
{%- for annotation in annotations_purple %}
{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]] 
{% endif %}
{% if annotation.annotatedText and not (annotation.tags.length > 0 and annotation.hashTags.includes("#writing_inspiration"))%}
> [!motivation]+ Motivation, Implementation detail, General comment<br>
> - [ ] Completed
> {{annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}

{% if annotations_red.length > 0 %}
{%- for annotation in annotations_red %}
{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]] 
{% endif %}
{% if annotation.annotatedText %}
> [!limitation]+ Limitations, Assumptions<br>
> - [ ] Completed
> {{annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}


{% if annotations_comment.length > 0 %}
{%- for annotation in annotations_comment %}
{%- if annotation.comment and not (annotation.tags.length > 0 and annotation.hashTags.includes("#writing_inspiration"))%}

> [!note]+ Personal notes<br>
> - [ ] Completed
> {{annotation.comment}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}

{% if annotations_comment.length > 0 %}
{%- for annotation in annotations_comment %}
{%- if (annotation.comment or annotation.annotatedText) and (annotation.tags.length > 0 and annotation.hashTags.includes("#writing_inspiration"))%}

> [!inspiration]+ Writing inspiration<br>
> - [ ] Completed
> {{annotation.comment if annotation.comment else annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}


{% if annotations_green.length > 0 %}
{%- for annotation in annotations_green %}
{% if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]] 
{% endif %}
{% if annotation.annotatedText %}
> [!literature]+ Literature<br>
> - [ ] Completed
> {{annotation.annotatedText}}
> [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{%- endfor %}
{% endif %}


{% endif %}
{% endpersist %} 

