---
title: Table of Contents & Sidebar Menu
type: essay
weight: 4650
abstract: "Adjust the styles of, and individual items in, Quire’s auto-generated contents lists"
---

## Table of Contents

To create a Table of Contents (TOC), add a Markdown file to your project with `type: contents` specified. If you add any Markdown to this file, it will be displayed as formatted text above the TOC list.

```yaml
title: Contents
weight: 2
type: contents
```

From there, Quire will automatically generate the TOC based on the structure of the files in your `content` directory (including assigned page weights and the organization of the section and sub-section directories) and the metadata of each page (the title, subtitle, contributors, etc.) Please see the [*Page Types & Structure*](/documentation/pages/) section of our documentation for more information.

### TOC Styles

There are four different TOC styles. A `class` value may be added to the page YAML to define the TOC format. The default TOC style class is `list`. The three other style classes available are `brief`, `abstract`, and `grid`.

```yaml
class: list
```

| Class | Description |
| --- | --- |
| `list` | The default style. Includes `label`, `title,`, `subtitle`, `contributor` information for each page. |
| `brief` | Will only show `title`, or if provided `short_title` for each page, and only for top-level pages and sections. Sub-sections will not display. |
| `abstract` | Includes everything in `list` as well as an `abstract` for each page if one is given. |
| `grid` | A graphic layout. Will show a “card” for each page. For `entry` pages, or other pages with `image` specified, the card will display the image, along with any `label`, `title,`, and `subtitle`, pages without an image specified will display only the text. |

{{< q-figure-group id="modern-contents-list, modern-contents-brief, modern-contents-abstract, modern-contents-grid" grid="2" >}}

### TOCs for Individual Sections

A `type: contents` page placed inside a section directory will display the contents just for that section, as well as any of its sub-sections. This can be useful, for example, in collection catalogues where you want a `grid` TOC displaying the objects in that catalogue section, or for a collected papers volume where you want to show the abstracts for the pages in the section.

### Removing Pages from the TOC

While the TOC is generated automatically by Quire based on the Markdown pages in your `content` directory, you can remove or hide pages from the TOC by adding `toc: false` to the YAML for that page. This might be done, for example, for the project’s cover page, which would not typically be included in a traditional book TOC. Or for sub-section pages deep in the book that may clutter the TOC. In any case, hiding the page from the TOC will not change how the page appears when navigating by the Next and Previous buttons and links. Nor will it keep the page from otherwise being linked to or viewed.

{{< q-class "box tip" >}}
Adding `toc: false` will only remove the page’s listing in the TOC. To entirely hide a page from Quire’s outputs use `online: false`, `pdf: false`, and `epub: false`.
{{< /q-class >}}

### Page Numbering in the PDF

When you output your project as a PDF, page numbers will automatically be added to the pages and to the corresponding entries in the Table of Contents.

The frontmatter pages of books are usually numbered in lowercase Roman numerals (i, ii, iii, iv, etc.). The Arabic numeral 1 is then assigned to the first page of true “content” for the book. Usually the first chapter, or an introduction. Quire handles things the same way.

To assign a particular section to be page 1 of your project, add `class: page-one` to the Markdown file. This tag means that this section is page 1 (in Arabic numerals), and everything before it is frontmatter and so will be numbered in lowercase Roman.

{{< q-class "box warning" >}}
Only one page in your project can have the `class: page-one` tag.
{{< /q-class >}}

## Sidebar Menu

Like the TOC, the sidebar Menu is generated automatically by Quire based on the structure of the files in your `content` directory and the metadata of each page.

Unlike the TOC, the Menu is a built-in part of every Quire project and does not have its own Markdown page.

There are two different Menu styles, `list` (the default) and `brief`, that match those in the [TOC styles](#toc-styles) listed previously. The Menu styles can be chosen with the `menuClass` setting in your Quire project's `config.yml` file.

```yaml
menuClass: list
```

### Removing Pages from the Menu

[As described with the TOC above](#removing-pages-from-the-toc), you can remove or hide pages from the Menu by adding `menu: false` to the YAML for that page.

### Menu Other Formats & Footer Links

Following the list of contents in the Menu is a section with download links for the other formats of your Quire project. These are listed in the `publication.yml` file of your project in the `resource_link` list. Any link listed here with a `type: other-format` will show up in the “Other Formats” link list in the Menu. The `name` attribute provides the text for the link as it appears.

```yaml
- type: other-format
  name: PDF
  media_type: application/pdf
  link_relation: alternate
  url: /downloads/output.pdf
```

Similarly, links in the bottom footer of the Menu, are also created from links listed in the `resource_link` list, but with `type: footer-link`.

```yaml
- type: footer-link
  name: Privacy Policy
  url: https://www.getty.edu/legal/privacy.html
```

Read more about [resource links in the *Metadata & Configuration* chapter](/documentation/metadata-configuration/#formats-resources--links) of this guide.

### Other Menu Items

The publisher logo, copyright statement, and license information found in the Menu are all generated from YAML in the `publication.yml` file of your project.

Read more about [copyright and licenses in the *Metadata & Configuration* chapter](/documentation/metadata-configuration/#copyright--license) of this guide.

Similarly, the “Cite This Page” feature in the Menu generates Chicago- and MLA-style citations for the current page based on YAML in the individual page itself, as well as that from the `publication.yml` file.

Read more about [citation-related YAML in the *Copyright & About Pages*](/documentation/copyright-about-pages/) chapter of this guide.
