# Electric Energy Systems Group Website

Welcome the the source repo for the EESG group website. This website is built
using Hugo and Wowchemy. To make routine edits / content additions, you just
need to add new markdown files following the existing folder structure.

More extensive template edits can be made by overriding the Wowchemy templates
as well, but this requires knowledge of HTML and potentially JavaScript.

## Local Build Instructions

Install the most recent **extended** version of Hugo from the source binaries
(especially on Ubuntu, since installing via `apt-get` will give you an older
version). Make sure you install the extended version as Wowchemy will not work
otherwise. You will also need to install go: `sudo snap install --classic go`

Then run `hugo server` from the repo root to preview the pages.

[Hugo install instructions](https://wowchemy.com/docs/getting-started/install-hugo-extended/)

### A Note About Building Large Files

We host many "large" (>10MB) PDF files of books and presentations. To keep the
repository lightweight, these files are in Dropbox. Large files should not be
added directly to the repository directly.

## Website Update Instructions

To make an update to a section of the website, first make a new git branch. You
will not be able to push your changes directly to main. Once you have made
the changes, verify that your content is how you want it to appear by running
`hugo server` and browsing the new website on your local machine.

Finally, open a pull request in Github to merge your changes into the main
branch. The hosted website should automatically update after your changes
are merged and built.

You should only have to modify files in `content/` to make updates. For more
detailed documentation, see the
[Wowchemy documentation](https://wowchemy.com/docs/)

### Adding PDF files

PDF files associated with content should have the same filename as their
parent folder. For example, to upload a PDF file of presentation slides, the
folder structure would look like
`content/presentation/name-of-presentation/name-of-presentation.pdf`. This will
automatically create a PDF button for that item in the content listview.

For PDF files in `content/reference_books/`, large groups of PDF files
(grouped seminar slides), or single PDFs greater than 20MB in side, you should
not add them directly to the repo but instead add them to the EESG-website
Dropbox and link to them using the `url_pdf` field.

Other PDFs can be added using `git add -f pathtopdf`. The `-f` flag is
necessary since **PDFs are ignored by default to prevent users from accidentally
committing huge PDFs (or data-sensitive PDFs) to the repository**.

### Creating a news post

News posts reside in `content/post`. You can add a featured image by uploading
an image named `featured.jpg` to the post object's folder. For announcements
that already have external webpages, you can avoid duplicating content with
the `external_link` key:

```yaml
---
title: Marija Ilic receives the IEEE PES Outstanding Power Engineering Educator award
date: 2020-08-04
image:
  focal_point: 'middle'
external_link: https://ieeetv.ieee.org/ieeetv-specials/ieee-pes-awards-2020-ieee-pes-outstanding-power-engineering-educator-award
profile: false
reading_time: false
---
```

For posts where you want to add text to the website itself, you can add it
using markdown after the yaml config. Only the text above the `<!--more-->`
section will show in post previews.

```yaml
---
title: Marija Ilic delivers keynote talk at 2019 FREEDM Research Symposium
date: 2019-10-12
image:
  focal_point: 'middle'
---
Prof. Marija Ilic was invited to deliver a keynote speech at the Future
Renewable Electric Energy Delivery and Management
([FREEDM](https://www.freedm.ncsu.edu/)) Research Symposium.

<!--more-->
Her presentation titled ‘The Future of Electric Power Grid ‘ can be found [here](https://www.freedm.ncsu.edu/wp-content/uploads/2019/04/Ilic-MIT-Future-of-the-Grid.pdf).
```

### Creating a project

- Pick a project name. The name should be all lowercase and use hyphens instead
  of spaces. The name will be used to link other items
  (publications, presentations) to the project.
- Make a new folder `content/project/projectname` (do not make a folder in `content/projects`)
- copy the following template to a file titled `index.md` in the project folder:


```yaml
---

title: ProjectTitleHere
# the authors should correspond to folder names in content/authors
authors:
  - author1
  - author2
# add 'ongoing' if the project is ongoing
tags:
  - ongoing
  - tag2
# Date the project started (approximate)
date: 2019-11-20T12:52:43-04:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# URL for external lines
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
# Your project description goes here. The text will be displayed via markdown.

A few sentences describing what the project is.

**Funding Agency:** Project funder
```

### Adding a group member

First, make a folder `content/authors/name` to store the member's
information. The `name` folder should be the member's last name, all lowercase.
The name of this folder is used to cross-reference their profile with the
`author` field in projects and publications.

Then, add their image as `content/authors/name/avatar.jpg` (PNG format
is also fine).

Finally, create the file `content/authors/name/_index.md`, filling in the
following:

```yaml
---
# Display name
title: First, Last

# Is this the primary user of the site?
superuser: False

# Role/position
role: Graduate Student, Postdoctoral Associate, etc.

# Organizations/Affiliations
organizations:
  - name: MIT Department of Electrical Engineering & Computer Science
    url: ''

# Comment out any items that are not applicable for the user.
social:
  - icon: envelope
    icon_pack: fas
    link: 'mailto:mit-email@mit.edu'
  - icon: google-scholar
    icon_pack: ai
    link: google scholar link here
  - icon: github
    icon_pack: fab
    link: github link here
  - icon: linkedin
    icon_pack: fab
    link: linkedin link here

# Highlight the author in author lists? (true/false)
highlight_name: true

# Organizational groups this person belongs to.
user_groups:
  - Postdocs
  - Grad Students
  - Previous PhD Students
  - Previous Masters Students
---

Member bio goes here.

```

### Creating a publication

Publications go in `content/publication`. First, create a folder in
`content/publication` with the prefix:

- `book-` for a book
- `paper-` for a journal or conference paper
- `patent-` for a patent
- `thesis-` for a thesis

Next, create a file `index.md` in that folder and fill out the following template.
To link the publication with one or more projects, add items under the
`projects` key.

```yaml
---
title: 'Publication Title'
# For authors who have a profile on the website, use their lowercase last name
# (what their folder is named in `content/authors`)
authors:
  - author1
  - author2
date: '15 July 2019'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2019-07-15T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['0']

# Publication name and optional abbreviated publication name.
publication: 'PublicationName'
publication_short: 'PublicationAbbreviation'

tags:
#   - Source Themes
featured: false

# links:
# - name: ""
#   url: ""
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides:
---
```

## Remote Build Process

Each time a commit is pushed to the `main` or `github-pages` branch, a
[Github action](https://github.com/features/actions) is triggered that runs
the hugo build and pushes the build files to the `gh-pages` branch of the
`mit-eesg.github.io` pages.

The build configuration can be viewed at `.github/workflows/gh-pages.yml`. You
should not need to change this file under normal situations. When Daniel Shen
leaves, the access token secret will need to be changed to somebody else's
action token.


## Miscellaneous Tips

### Hyperlinking

Relative hyperlinks are supported. For example, having a markdown link in the
file `content/post/postid/_index.md`

```
[linktext](another/level)
```

Will link to the page `domain.com/post/postid/another/level`. This can be
useful for linking to supplementary pages or content.

### Overriding layouts

TODO: Fill out