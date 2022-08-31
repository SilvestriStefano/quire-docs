---
title: Copyright & About Pages
weight: 5200
type: essay
abstract: "Create Chicago and MLA formatted citations for your publication"
---

## Cite this Page

The Chicago and MLA formatted citations provided on every page of the online edition of a Quire publication are generated automatically based on data in your publication.yml file, and in the YAML of each Markdown page.

Key metadata about your publication that is included in publication.yml and will be used to generate your citations:

```yaml
title:
subtitle:
reading_line:

series:
number_in_series:

pub_date: YYYY-MM-DD

identifier:
  url:

contributor:
- id:
  type:
  role:
  first_name:
  last_name:
  full_name:
```

Key metadata about individual pages/chapters included in the YAML of the specific Markdown page:

```yaml
title:
subtitle:
contributor:
- id:
  first_name:
  last_name:
  full_name:
```

- For names, you need either first_name AND last_name, or just full_name
- Contributors identified as type: primary will be included in the citation as the publication’s authors
- If your publication has one or more editors, rather than authors, they should be type: primary, and role: editor in the YAML.

For more information see the chapter on [Contributors](/documentation/contributors/)
