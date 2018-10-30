* Homework

Modelling BBC web site

** Relationships

A section can have many subsections
[Section] 1 <---> 1..Many [Subsection]

An article can belong to a subsection
[Article] 1 <---> 1 [Subsection]

An article has one or more authors. An author can appear as a byline on many articles
[Article] Many <---> Many [Author]


** Sections

A section of the news (top-level) e.g. Business, UK, World, Science, etc

- section_id : serial
- name (e.g. UK, Business, Health, Science) : string

** Subsections

A sub-section of a second (e.g. under UK, Scotland
"England" and "Wales" are subsections. Under Business,
subsections are "Your Money" and "Markets")

- subsection_id : serial
- section_id: Foreign Key sections(section_id)
- Name : string e.g. (Under UK, Scotland, NI etc)

** Articles

We assume articles only get stored in one subsections
In reality this is probably a 1:Many relationship with
subsection.

- article_id : serial primary_key
- headline: string
- published_date: string
- content: string
- subsection: foreign key subsections(subsection_id)

** Authors

An individual writer (e.g. freelance, staff)

- author_id : serial primary_key
- name : string

** Authorship

handles Many:Many between Authors and Articles

- author_id:  foreign key authors(author_id)
- article_id: foreign key articles(article_id)
